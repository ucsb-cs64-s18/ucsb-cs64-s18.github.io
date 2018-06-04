---
layout: lab
num: lab09
ready: true
desc: "Finite State Machines"
assigned: 2018-06-04 08:00:00.00-7
due: 2018-06-08 23:59:59.00-7
---
<h1>Lab 9: Finite State Machines</h1>
<hr>
<p>Due Friday, May 8 at 11:59:59 PM</p>

<h2>Goals for This Week</h2>
<p>By the time you have completed this work, you should be able to:</p>
<ul>
  <li>Draw a finite state diagram corresponding to a basic word problem</li>
  <li>Demonstrate your ability to implement this state diagram via a circuit</li>
</ul>

<b>Provided files:</b>
<ul>
  <li><a href="partner.txt"><code>partner.txt</code></a></li>
</ul>

<!-- DOCUMENTATION -->

<hr>
<h2>Step by Step Instructions</h2>
<p>
  For this week, you will translate a word problem into a diagram representing a finite state machine (FSM).
  From there, you will provide enough detail to implement the finite state machine as a circuit.
  There are multiple tasks for this assignment.
  While each task can be completed independently of each other, they progressively build in difficulty, so it is recommended to complete them in order.
  The tasks are listed below:
</p>

<ul>
  <li>Task 1: Design a FSM For a Digital Display</li>
  <li>Task 2: Design a FSM to Recognize <code>01</code></li>
  <li>Task 3: Design a FSM to Recognize <code>0110</code></li>
  <li>Task 4: Design a FSM for a Vending Machine</li>
</ul>

<p>
  The initial step below describes how to get the files you will need into the appropriate place.
  These files are used for all the different tasks.
</p>

<h3>Initial Step: Create a Directory for This Lab and Copy Over the Files</h3>
<p>After you log in, go into your <code>cs64</code> directory that you created last time:</p>
<pre>
cd cs64
</pre>
<p>Then create a new directory for this lab: <code>lab9</code>:</p>
<pre>
mkdir lab9
</pre>
<p>Then go into that directory.</p>
<p>Now copy over all of the files necessary for this week's tasks:</p>
<pre>
cp ~zmatni/public_html/cs64s18/labs/9/partner.txt .
</pre>
<p>
  Note the use of the trailing <code>.</code> in the above command, which stipulates that the specified files should be copied into the current directory.
</p>

<h2>Task 1: Design a FSM For a Digital Display</h2>
<p>
  In this task, you will design a FSM which controls a seven segment display.
  Throughout this task, we will be using a seven segment display similar to the following (provided by <a href="https://en.wikipedia.org/wiki/Seven-segment_display">Wikipedia</a>):
</p>
<img src="7_segment_display.png">
<p>
  Each of the letters in the above diagram refers to an individual segment of the display.
  The identifier &ldquo;<code>DP</code>&rdquo; refers to the decimal point, which will not be used in this task.
  The display allows segments to be individiually turned on and off, allowing for different numbers to be represented by selectively enabling or disabling the right segments.
  The table below illustrates which segments need to be enabled for the corresponding decimal digit to be represented:
</p>
<table border="1">
  <tr>
    <th>Number</th>
    <th>Segments to Enable</th>
  </tr>
  <tr>
    <td><code>0</code></td>
    <td><code>A, B, C, D, E, F</code></td>
  </tr>
  <tr>
    <td><code>1</code></td>
    <td><code>B, C</code></td>
  </tr>
  <tr>
    <td><code>2</code></td>
    <td><code>A, B, G, E, D</code></td>
  </tr>
  <tr>
    <td><code>3</code></td>
    <td><code>A, B, G, C, D</code></td>
  </tr>
  <tr>
    <td><code>4</code></td>
    <td><code>F, B, G, C</code></td>
  </tr>
  <tr>
    <td><code>5</code></td>
    <td><code>A, F, G, C, D</code></td>
  </tr>
  <tr>
    <td><code>6</code></td>
    <td><code>A, F, G, E, C, D</code></td>
  </tr>
  <tr>
    <td><code>7</code></td>
    <td><code>A, B, C</code></td>
  </tr>
  <tr>
    <td><code>8</code></td>
    <td><code>A, B, C, D, E, F, G</code></td>
  </tr>
  <tr>
    <td><code>9</code></td>
    <td><code>A, B, C, D, F, G</code></td>
  </tr>
</table>

<p>
  The FSM for this task should alternate between displaying <code>1</code>, <code>2</code>, <code>4</code>, and <code>8</code>, in that order, and without the application of any external input (in other words, you go from one state to another on just the "tick" of the clock).
  In order to accomplish this, the inputs to the seven segment display will be treated as outputs of your FSM.
  That is, your FSM will output the appropriate values of <code>A</code>, <code>B</code>, <code>C</code>, <code>D</code>, <code>E</code>, <code>F</code>, and <code>G</code> in order to represent the numbers of interest.
  This overall task is separated into a series of questions, which should be submitted digitally via the <code>turnin</code> command.
</p>
<ol>
  <li>
    <p>
      Draw the finite state machine corresponding to this task.
      If you are submitting this online, put this diagram into a file named &ldquo;<code>display.jpg</code>&rdquo;.
    </p>
  </li>
  <li>
    <p>
      How many latches/flip-flops do you need to implement this state machine?
      (Hint: this corresponds to the number of bits necessary in order to encode all possible states uniquely.)
      If you are submitting this online, put this into a file named &ldquo;<code>display.txt</code>&rdquo;.
      This will be read by hand, so don't worry about the formatting (as long as it is clear and unambiguous).
    </p>
  </li>
  <li>
    <p>
      Draw a single truth table representing the behavior of the state machine.
      Be sure to label your states in binary.
      Your table should have inputs corresponding to whatever state you are in.
      The output corresponds to the next state to enter for a given input state, along with the values for the seven segment display.
      If you are submitting this online, add this to your &ldquo;<code>display.txt</code>&rdquo; file.
      This will be read by hand, so don't worry about the formatting (as long as it is clear and unambiguous).
    </p>
  </li>
  <li>
    <p>
      Using a Karnaugh map, determine the minimal sum-of-products formula corresponding to output <code>A</code> (corresponding to input <code>A</code> of the seven-segment display.
      Where appropriate, use <i>don't cares</i> in the map (note that there may be no appropriate uses of <i>don't cares</i>).
      If you are submitting this online, add this to your &ldquo;<code>display.txt</code>&rdquo; file.
      This will be read by hand, so don't worry about the formatting (as long as it is clear and unambiguous).
    </p>
  </li>
  <li>
    <p>
      Using a Karnaugh map, determine the minimal sum-of-products formula corresponding to the rightmost bit of the next state.
      Where appropriate, use <i>don't cares</i> in the map (note that there may be no appropriate uses of <i>don't cares</i>).
      If you are submitting this online, add this to your &ldquo;<code>display.txt</code>&rdquo; file.
      This will be read by hand, so don't worry about the formatting (as long as it is clear and unambiguous).
    </p>
  </li>
</ol>

<p>
  To help with questions 1-3, a solution to a very similar problem is provided <a href="display_example.jpg">here</a>.
  In this example, the FSM alternates between displaying <code>1</code> and <code>7</code>.
  The diagram has these major components:
</p>
<ul>
  <li>
    Circles, representing the different states of the FSM.
    These are written in black.
    Each state has the following information written on it:
    <ul>
      <li>
        A human-readable label, written in purple.
        The labels chosen for this example correspond to whether the state displays a <code>1</code> or a <code>7</code>.
      </li>
      <li>
        A binary label, shown in parentheses and written in green.
        Each state needs a unique binary label, which is used in the truth table (shown in red at the bottom of the image).
      </li>
      <li>
        The output of the state, underlined and written in blue.
        For example, in state <code>7</code> (binary <code>1</code>), the output of the state is <code>ABC</code>, meaning segments <code>A</code>, <code>B</code>, and <code>C</code> in the seven-segment display should be activated.
        In conjunction, when these three segments are lit up, they display <code>7</code>.
      </li>
    </ul>
  </li>
  <li>
    Arrows, representing transitions between different states of the FSM.
    Transitions occur on clock ticks, which are provided by an unseen (but implicitly present) clock.
  </li>
</ul>

<h2>Task 2: Design a FSM to Recognize <code>01</code></h2>
<p>
  In this task, you will design a FSM which will set a particular output <code><b>U</b></code> to <code>1</code> each time <code>01</code> is encountered in a stream of inputs.
  Inputs are specified one at a time, and are represented by the variable <code><b>I</b></code>.
  To illustrate, consider the following example, which shows different values of <code><b>U</b></code> and <code><b>I</b></code> over time, where each cell is separated by a clock tick:
</p>
<table border="1">
  <tr>
    <td><code><b>I</b></code></td>
    <td><code>1</code></td>
    <td><code>0</code></td>
    <td><code>1</code></td>
    <td><code>1</code></td>
    <td><code>0</code></td>
    <td><code>0</code></td>
    <td><code>1</code></td>
    <td><code>1</code></td>
    <td><code>0</code></td>
    <td><code>1</code></td>
    <td><code>0</code></td>
    <td><code>1</code></td>
    <td><code>1</code></td>
  </tr>
  <tr>
    <td><code><b>U</b></code></td>
    <td><code>0</code></td>
    <td><code>0</code></td>
    <td><code>0</code></td>
    <td><code>1</code></td>
    <td><code>0</code></td>
    <td><code>0</code></td>
    <td><code>0</code></td>
    <td><code>1</code></td>
    <td><code>0</code></td>
    <td><code>0</code></td>
    <td><code>1</code></td>
    <td><code>0</code></td>
    <td><code>1</code></td>
  </tr>
</table>

<p>
  In the above example, it may appear that the output of <code><b>U</b></code> is delayed with respect to input <code><b>I</b></code>.
  That is, when the <code>1</code> is <code>01</code> is encountered, it's not until the <i>next</i> clock tick that <code><b>U</b></code> is set to <code>1</code>.
  This is actually expected behavior, as it reflects the fact that first the circuit reads <code>1</code>, and then it moves into a state that reports <code><b>U</b> = 1</code>.
</p>

<p>
  The key difference between this task and Task 1 is that this circuit takes an auxilliary input, which changes over time.
  As such, the finite state machine diagrams you draw should reflect changes in behavior, depending on which inputs are provided.
  Ultimately, this means that your FSMs will transition to different states depending on the inputs provided.
</p>

<p>
  This overall task is separated into a series of questions, which should be submitted digitally via the <code>turnin</code> command.
</p>
<ol>
  <li>
    <p>
      Draw the finite state machine corresponding to this task.
      If you are submitting this online, put this diagram into a file named &ldquo;<code>sequence1.jpg</code>&rdquo;.
    </p>
  </li>
  <li>
    <p>
      How many latches/flip-flops do you need to implement this state machine?
      (Hint: this corresponds to the number of bits necessary in order to encode all possible states uniquely.)
      If you are submitting this online, put this into a file named &ldquo;<code>sequence1.txt</code>&rdquo;.
      This will be read by hand, so don't worry about the formatting (as long as it is clear and unambiguous).
    </p>
  </li>
  <li>
    <p>
      Draw a single truth table representing the behavior of the state machine.
      Be sure to label your states in binary.
      Your table should have inputs corresponding to whatever state you are in, along with <code><b>I</b></code>.
      The output corresponds to the next state to enter for a given input state, along with <code><b>U</b></code>.
      If you are submitting this online, add this to your &ldquo;<code>sequence1.txt</code>&rdquo; file.
      This will be read by hand, so don't worry about the formatting (as long as it is clear and unambiguous).
    </p>
  </li>
  <li>
    <p>
      Using a Karnaugh map, determine the minimal sum-of-products formula corresponding to output <code><b>U</b></code>.
      Where appropriate, use <i>don't cares</i> in the map (note that there may be no appropriate uses of <i>don't cares</i>).
      If you are submitting this online, add this to your &ldquo;<code>sequence1.txt</code>&rdquo; file.
      This will be read by hand, so don't worry about the formatting (as long as it is clear and unambiguous).
    </p>
  </li>
  <li>
    <p>
      Using a Karnaugh map, determine the minimal sum-of-products formula corresponding to the rightmost bit of the next state.
      Where appropriate, use <i>don't cares</i> in the map (note that there may be no appropriate uses of <i>don't cares</i>).
      If you are submitting this online, add this to your &ldquo;<code>sequence1.txt</code>&rdquo; file.
      This will be read by hand, so don't worry about the formatting (as long as it is clear and unambiguous).
    </p>
  </li>
</ol>

<p>
  To help with questions 1-3, a solution to a very similar problem is provided.
  The state diagram is <a href="sequence1_fsm.jpg">here</a>, and the corresponding truth table is <a href="sequence1_truth_table.jpg">here</a>.
  The only difference between Task 2 and this provided solution is that the provided solution recognizes <code>10</code> as opposed to <code>01</code>.
</p>

<h2>Task 3: Design a FSM to Recognize <code>0110</code></h2>
<p>
  In this task, you will design a FSM which will set a particular output <code><b>U</b></code> to <code>1</code> each time <code>0110</code> is encountered in a stream of inputs.
  Inputs are specified one at a time, and are represented by the variable <code><b>I</b></code>.
  To illustrate, consider the following example, which shows different values of <code><b>U</b></code> and <code>I</code> over time, where each cell is separated by a clock tick:
</p>
<table border="1">
  <tr>
    <td><code><b>I</b></code></td>
    <td><code>1</code></td>
    <td><code>0</code></td>
    <td><code>1</code></td>
    <td><code>1</code></td>
    <td><code>0</code></td>
    <td><code>0</code></td>
    <td><code>1</code></td>
    <td><code>1</code></td>
    <td><code>0</code></td>
    <td><code>1</code></td>
    <td><code>0</code></td>
    <td><code>1</code></td>
    <td><code>1</code></td>
    <td><code>0</code></td>
    <td><code>1</code></td>
    <td><code>1</code></td>
    <td><code>0</code></td>
    <td><code>1</code></td>
    <td><code>1</code></td>
    <td><code>0</code></td>
    <td><code>1</code></td>
  </tr>
  <tr>
    <td><code><b>U</b></code></td>
    <td><code>0</code></td>
    <td><code>0</code></td>
    <td><code>0</code></td>
    <td><code>0</code></td>
    <td><code>0</code></td>
    <td><code>1</code></td>
    <td><code>0</code></td>
    <td><code>0</code></td>
    <td><code>0</code></td>
    <td><code>1</code></td>
    <td><code>0</code></td>
    <td><code>0</code></td>
    <td><code>0</code></td>
    <td><code>0</code></td>
    <td><code>1</code></td>
    <td><code>0</code></td>
    <td><code>0</code></td>
    <td><code>1</code></td>
    <td><code>0</code></td>
    <td><code>0</code></td>
    <td><code>1</code></td>
  </tr>
</table>

<p>
  In the above example, it may appear that the output of <code><b>U</b></code> is delayed with respect to input <code><b>I</b></code>.
  That is, when the <code>1</code> is <code>0110</code> is encountered, it's not until the <i>next</i> clock tick that <code><b>U</b></code> is set to <code>1</code>.
  This is actually expected behavior, as it reflects the fact that first the circuit reads <code>1</code>, and then it moves into a state that reports <code><b>U</b> = 1</code>.
</p>

<p>This overall task is separated into a series of questions, which may be submitted digitally via turnin:</p>
<ol>
  <li>
    <p>
      Draw the finite state machine corresponding to this task.
      If you are submitting this online, put this diagram ito a file named &ldquo;<code>sequence2.jpg</code>&rdquo;.
    </p>
  </li>
  <li>
    <p>
      How many latches/flip-flops do you need to implement this state machine?
      (Hint: this corresponds to the number of bits necessary in order to encode all possible states uniquely.)
      If you are submitting this online, put this into a file named &ldquo;<code>sequence2.txt</code>&rdquo;.
      This will be read by hand, so don't worry about the formatting (as long as it is clear and unambiguous).
    </p>
  </li>
  <li>
    <p>
      Draw a single truth table representing the behavior of the state machine.
      Be sure to label your states in binary.
      Your table should have inputs corresponding to whatever state you are in, along with <code><b>I</b></code>.
      The output corresponds to the next state to enter for a given input state, along with <code><b>U</b></code>.
      If you are submitting this online, add this to your &ldquo;<code>sequence2.txt</code>&rdquo; file.
      This will be read by hand, so don't worry about the formatting (as long as it is clear and unambiguous).
    </p>
  </li>
  <li>
    <p>
      Using a Karnaugh map, determine the minimal sum-of-products formula corresponding to output <code>U</code>.
      Where appropriate, use <i>don't cares</i> in the map (note that there may be no appropriate uses of <i>don't cares</i>).
      If you are submitting this online, add this to your &ldquo;<code>sequence2.txt</code>&rdquo; file.
      This will be read by hand, so don't worry about the formatting (as long as it is clear and unambiguous).
    </p>
  </li>
  <li>
    <p>
      Using a Karnaugh map, determine the minimal sum-of-products formula corresponding to the rightmost bit of the next state.
      Where appropriate, use <i>don't cares</i> in the map (note that there may be no appropriate uses of <i>don't cares</i>).
      If you are submitting this online, add this to your &ldquo;<code>sequence2.txt</code>&rdquo; file.
      This will be read by hand, so don't worry about the formatting (as long as it is clear and unambiguous).
    </p>
  </li>
</ol>

<p>
  Note the similarity between this task and Task 2.
  Task 3 ends up doing something very similar to both Task 2 and the example solution provided for the task similar to Task 2.
  That said, be sure to take into account the differences.
  Pay particularly close attention to where transitions should go which move &ldquo;backwards&rdquo; in the FSM.
  That is, it is expected that you'll have transitions which go to previously observed states, and these transitions won't necessarily all return to the same state.
</p>

<h2>Task 4: Design a FSM for a Vending Machine</h2>
<p>
  In this task, you will design a FSM for a simple (albeit strange) vending machine of office supplies.
  The vending machine sells three possible items, each at a different cost:
</p>
<table border="1">
  <tr>
    <th>Item</th>
    <th>Cost</th>
  </tr>
  <tr>
    <td>Pencil</td>
    <td>10 cents</td>
  </tr>
  <tr>
    <td>Eraser</td>
    <td>20 cents</td>
  </tr>
  <tr>
    <td>Pen</td>
    <td>30 cents</td>
  </tr>
</table>

<p>
  The vending machines accepts nickels (worth 5 cents), dimes (worth 10 cents), and quarters (worth 25 cents).
  Physically, it is only possible to insert a single coin at a time.
  The vending machine features a large button labeled &ldquo;<code>DONE</code>&rdquo;, which, when pressed, will dispense the most expensive item which can be purchased with the input money.
  For example, if a dime and two nickels had been entered (totalling 20 cents), then it would dispense an eraser upon pressing &ldquo;<code>DONE</code>&rdquo;.
  Once an item is dispensed, the vending machine returns to an initial state wherein it shows that no money has been inserted.
</p>

<p>
  To help simplify things, the vending machine does not provide any change.
  This means that any additional money provided will be lost.
  For example, if a quarter had been entered and then &ldquo;<code>DONE</code>&rdquo; pressed, the vending machine would dispense an eraser (because this is the most expensive item which can be purchased with 25 cents), and then the vending machine would return to the point where it shows that no money has been entered.
  As another example, if two quarters had been entered, then upon pressing &ldquo;<code>DONE</code>&rdquo;, it would dispense a pen (the most expensive item purchasable with 50 cents), and then the vending machine would return to the point where it shows that no money has been entered.
</p>

<p>While there are different ways to model these different parameters as inputs, your FSM should deal with the following inputs:</p>

<table border="1">
  <tr>
    <th>Input</th>
    <th>Description</th>
  </tr>
  <tr>
    <td><b><code>K</code></b></td>
    <td>Set to <code>1</code> if a nickel has been entered, else <code>0</code></td>
  </tr>
  <tr>
    <td><b><code>D</code></b></td>
    <td>Set to <code>1</code> if a dime has been entered, else <code>0</code></td>
  </tr>
  <tr>
    <td><b><code>Q</code></b></td>
    <td>Set to <code>1</code> if a quarter has been entered, else <code>0</code></td>
  </tr>
  <tr>
    <td><b><code>E</code></b></td>
    <td>Set to <code>1</code> if &ldquo;<code>DONE</code>&rdquo; has been pressed, else <code>0</code></td>
  </tr>
</table>

<p>
  In addition to the above inputs, you'll also need to specify what the current state is, which should be indicated with inputs <b><code>C0</code></b> through <b><code>CN</code></b>, where <code>N</code> is the position of the greatest possible bit in your state encoding.
  For example, if you needed eight states in your FSM, then you'd have inputs <b><code>C0</code></b>, <b><code>C1</code></b>, and <b><code>C2</code></b>, as eight states can be uniquely encoded using three bits.
</p>

<p>
  Similarly to the inputs, the output parameters can be modeled in different ways.
  However, for the sake of consistency across different solutions, your FSM should deal only with the following outputs:
</p>

<table border="1">
  <tr>
    <th>Output</th>
    <th>Description</th>
  </tr>
  <tr>
    <td><b><code>DPENCIL</code></b></td>
    <td>
      Short for &ldquo;Dispense Pencil&rdquo;.
      Set to <code>1</code> if we should dispense a pencil, else <code>0</code>.
    </td>
  </tr>
  <tr>
    <td><b><code>DERASER</code></b></td>
    <td>
      Short for &ldquo;Dispense Eraser&rdquo;.
      Set to <code>1</code> if we should dispense an eraser, else <code>0</code>.
    </td>
  </tr>
  <tr>
    <td><b><code>DPEN</code></b></td>
    <td>
      Short for &ldquo;Dispense Pen&rdquo;.
      Set to <code>1</code> if we should dispense a pen, else <code>0</code>.
    </td>
  </tr>
</table>

<p>
  In addition to the above outputs, you'll also need to specify what the next state is, which should be indicated with outputs <b><code>N0</code></b> through <b><code>NM</code></b>, where <code>M</code> is the position of the greatest possible bit in your state encoding.
  For example, if you needed eight states in your FSM, then you'd have inputs <b><code>N0</code></b>, <b><code>N1</code></b>, and <b><code>N2</code></b>, as eight states can be uniquely encoded using three bits.
</p>

<p>This overall task is separated into a series of questions, which should be submitted via turnin:</p>
<ol>
  <li>
    <p>
      Draw the finite state machine corresponding to this task.
      If you are submitting this online, put this diagram ito a file named &ldquo;<code>vending.jpg</code>&rdquo;.
    </p>
  </li>
  <li>
    <p>
      How many latches/flip-flops do you need to implement this state machine?
      (Hint: this corresponds to the number of bits necessary in order to encode all possible states uniquely.)
      If you are submitting this online, put this into a file named &ldquo;<code>vending.txt</code>&rdquo;.
      This will be read by hand, so don't worry about the formatting (as long as it is clear and unambiguous).
    </p>
  </li>
  <li>
    <p>
      Draw a single truth table representing the behavior of the state machine.
      Be sure to label your states in binary.
      Your table should have inputs and outputs corresponding to the inputs and outputs described previously.
      If you are submitting this online, add this to your &ldquo;<code>vending.txt</code>&rdquo; file.
      This will be read by hand, so don't worry about the formatting (as long as it is clear and unambiguous).
    </p>
    <p>
      To simplify things, you may put <i>don't cares</i> where appoproiate in the <b>inputs</b>.
      For example, because it is physically impossible to insert more than a single coin at a time, if input <code>K = 1</code> (indicating a nickel has been inserted), then inputs <code>D</code> and <code>Q</code> can be safely labeled as <i>don't cares</i>, as implicitly they should always be <code>0</code> (and in reality we ignore their values entirely in this situation).
      With this setup, we can cut down on the number of repeated rows; instead of having two rows which differ in only whether or not <code>Q</code> is set, we can have a single row where <code>Q = <b>X</b></code>.
    </p>
  </li>
</ol>

<h3>Task 4 Hints</h3>
<p>The following are a series of hints which may be of use while implementing Task 4:</p>
<ul>
  <li>
    <p>
      You may assume only one coin is ever entered at a time.
      For example, this means that if <code>D = 1</code> (indicating a dime was entered), then it is guaranteed that <code>K = 0</code> and <code>Q = 0</code> (indicating a nickel and a quarter were not entered, respectively).
      Similarly, you don't need to worry about the user inputting multiples of the same coin at once (e.g., two quarters at once), which does not have a possible encoding in this setup.
      The practical advantage of this assumption is that transitions will only ever depend on one input at a time; you'll never need a transition which corresponds to the user inputting a combination of coins.
    </p>
  </li>
  <li>
    <p>
      You may assume that &ldquo;<code>DONE</code>&rdquo; is pressed only after all coins have been entered.
      Similar to the previous assumption, this means you don't need to worry about a case where the user inputs a coin while simultaneously pressing &ldquo;<code>DONE</code>&rdquo;.
      For example, if <code>E = 1</code>, then it is guaranteed that <code>K = 0</code> (meaning no nickels were inserted).
    </p>
  </li>
  <li>
    <p>
      You may assume that when &ldquo;<code>DONE</code>&rdquo; is pressed, the user will provide no more input until the vending machine has finished dispensing the most expensive item purchasable with the input money.
      This means that until the vending machine returns to the original state it started in with no input money, <code>K = 0</code>, <code>D = 0</code>, <code>Q = 0</code>, and <code>E = 0</code>.
    </p>
  </li>
  <li>
    <p>
      You may assume that the vending machine does not provide any change, and gives no indication to the user when money has simply been eaten.
      As with the example before, this means that if more money was provided than needed (e.g., providing 25 cents to purchase a 20 cent eraser), then the additional money simply disappears.
      Similarly, if the user does not provide enough money to purchase anything (e.g., inserting only a nickel and subsequently pressing &ldquo;<code>DONE</code>&rdquo;), then no items should be dispensed, but the vending machine will still return to the initial state.
    </p>
  </li>
  <li>
    <p>
      To help keep your diagrams clean, you need only indicate outputs when the output would be <code>1</code>.
      For example, if in one particular state a pencil should be dispensed, then in this particular state <b><code>DPENCIL</code></b> should be indicated.
      In all other states, simply omitting <b><code>DPENCIL</code></b> is equivalent to outputting that <code>DPENCIL = 0</code>.
    </p>
  </li>
  <li>
    <p>
      As for what your states in this vending machine indicate, probably the simplest approach is to have a distinct state for each amount of currency which can be deposited.
      At the very least, this means having states corresponding to 5 cents deposited, 10 cents deposited, 15 cents deposited, and so on.
      While your vending machine will likely need more states than this, the bulk of the states work in this fashion.
    </p>
  </li>
  <li>
    <p>
      Technically, a user can input an arbitrarily large amount of money into the machine.
      However, you don't need to worry about this too much, as the vending machine only dispenses one item at a time, and provides no change.
      As such, inputting 30 cents (enough to buy a pen, the most expensive item), is no different than inputting 35 cents or more.
    </p>
  </li>
</ul>

<h2>Turn in Everything Using <code>turnin</code></h2>
<p>
  <b>If you partnered with someone, record the email address they are using for the class in <code>partner.txt</code>.</b>
  For example, if your partner had the email address <a href="foo@bar.com">foo@bar.com</a>, then the contents of <code>partner.txt</code> should be the following (and <b>only</b> the following):
</p>
<pre>
Partner: foo@bar.com
</pre>
<p>If you did not partner with anyone, you do not need to (and should not) edit <code>partner.txt</code>.</p>

<p>Assuming you are in the <code>cs64/lab9</code> directory you created at the beginning, you can send in your answers <b>with the FSM images and answers</b> via the following command:</p>
<pre>
turnin lab9@cs64 display.jpg display.txt sequence1.jpg sequence1.txt sequence2.jpg sequence2.txt vending.jpg vending.txt
</pre>

<p>
  You may turn in the same assignment up to 100 times, which is useful if you are working on it incrementally.
  Note that only the last version you submitted will be graded.
</p>

<p>Even if you did not partner with anyone, you should still turn in <code>partner.txt</code>, which should not have been modified.</p>

<hr>
<blockquote>
  <p><font size="1">
  Copyright 2018, Ziad Matni, CS Dept, UC Santa Barbara. Adapted from work by Diana Franklin and Kyle Dewey. Permission to copy for non-commercial, non-profit, educational purposes granted, provided appropriate credit is given;  all other rights reserved.
  </font></p>
</blockquote>
