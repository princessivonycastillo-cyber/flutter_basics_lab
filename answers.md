
### GitHub repository link
https://github.com/princessivonycastillo-cyber/flutter_basics_lab

### Last three build() called lines (Activity 2):
build() called: 4 glasses
build() called: 5 glasses
build() called: 6 glasses

### Observations

### Activity 2: setState experiment
I removed `setState()` from `_addGlass()`, leaving only `if (_glasses < _goal) _glasses++;`, and tapped the + button several times. The number on the screen stayed the same and the progress bar did not move. This happened because `_glasses` did change in memory, but without `setState()` Flutter was never told that the data had changed. Since `build()` did not run again, the screen was not redrawn. When I put `setState()` back, the number and progress bar updated normally after every tap.

### Activity 3: Expanded experiment
When I removed Expanded from the Wind StatBox, that box shrank to the width of its content, while the other three boxes still split the remaining space, so they were no longer equal. Expanded makes a widget fill its share of the extra space in a Row or Column.

### Activity 4: crossAxisCount experiment
I changed crossAxisCount from 2 to 3. The grid showed three cards per row and each card became narrower. I changed it back to 2 afterwards. This happens because crossAxisCount sets the number of columns, so more columns means the same width is split into narrower cards.

### Activity 5: buildTheme experiment
I changed the ElevatedButton corner radius in buildTheme() from 8 to 20. The Elevated button now has much rounder corners. Because the style is set once in the theme, every ElevatedButton in the app changes at the same time without editing each button.


### Review Questions Answers
1. A StatelessWidget has no data that changes after it is built. It draws the same thing every time unless its parent gives it new inputs. A StatefulWidget holds data that can change while the app runs, and it redraws when that data changes. Example from this lab: the profile screen in Activity 1 is stateless, and the water tracker in Activity 2 is stateful because it counts glasses.

2. A StatefulWidget has two classes because the widget itself can’t store changing data. The first class (the StatefulWidget) just creates the state and holds the settings. The second class (the State) stores the variables like _glasses, has the setState() call, and has the build() method that draws the screen.

3. When I changed _glasses outside setState(), the number on the screen didn’t change. This is because Flutter doesn’t know it needs to rebuild the screen unless setState() is called. The value changed in the code, but the UI stayed the same until the next setState().

4. build() is called once when the app first loads (the “0 glasses” line), and then again every time I press the button and setState() runs. That’s why the Debug Console shows 1, 2, 3, 4, 5, and 6 glasses.

5. In a Row, the main axis goes left to right and the cross axis goes up and down. In a Column it’s the opposite: the main axis goes up and down and the cross axis goes left to right.

6. When I removed Expanded from the Wind StatBox, that box shrank to the width of its content, while the other three boxes still split the remaining space, so they were no longer equal. Expanded makes a widget fill its share of the extra space in a Row or Column.

7. We use GridView.builder because it only builds the items that are visible on the screen, so it’s faster and uses less memory. A Column builds everything at once, can’t scroll by itself, and can overflow if there are too many items.

8. Stack lets widgets sit on top of each other, so the Best seller badge can be placed over the menu card. Positioned sets exactly where the badge goes inside the Stack, like the top right corner, using top and right.

9. ThemeData changes the look of the whole app at once, like the main color or text style. A style on one widget only changes that widget. An example of ThemeData is setting the seedColor in buildTheme, and an example of a single-widget style is adding a TextStyle with a bigger fontSize to one Text.

10. The state (like isDark) is held in the main app widget that is a StatefulWidget, above MaterialApp. When I flip the switch, it calls setState() in that widget, which rebuilds MaterialApp with the new theme, so the whole app changes to dark mode. 

