# CSS — A few things I didn’t learn in the ‘tutorials’

I’ve spent some time trying to figure out some new styling in CSS that isn’t always standard in the ‘book’ or tutorials.

### CLEARFIX

Before the fun… An important task I wanted to solve is when we have a parent element whose children extend outside of the its div/box/region. What does this mean? We’re basically forcing an element to self-clear its floating children.

```css
/* Parent CSS Tag */
.parent:after {
  content: "";
  display: table;
  clear: both;
}
```

```html
 <!-- Here we’ll clear any floats in the HTML -->
<div class=“parent">
  <div class=“floated-child1"></div>
  <div class="floated-child2"></div>
  <div class="floated-child3"></div>
</div>
```

### 1. OUTLINE!
This had me plagued (for a hot 5 minutes). I was all excited to style my own input borders and be all crafty however every time I focused on the element I’d notice a little blue border around it. The solution is in the outline property.

[![Input onfocus example](http://www.robhitt.com/blog/four-css-tricks/images/input-focus.png)](https://youtu.be/yNbfLoVJWkw)


```css
/* Set that nice yellow background to the input box */
input[type="text"] {
  background-color: rgb(250, 255, 189);
}
/* The main point here is to set the border attributes to give it that nice grey smooth look */
input.outline {
  padding: .5em .75em;
  width: 30%;
  display: inline-block;
  font-size: 1.25em;
  font-family: "Avenir Next W01", "Avenir", sans-serif;
  font-weight: 700;
  border: 0.25em solid #eee;
  border-radius: 0.5em;
  color: rgb(0,0,0);
}
/* Set the buttery blue border color on focus */
input[type="text"]:focus {
  border-color: #09f;
}
/* Here's the missing link, if you want that light blue hazy outline gone on your input field then set the outline to 0px*/
input[type="text"]:focus.no-outline {
  outline: 0px;
}
```

#### PS. A friend just let me know the importance of the  outline is that it is an accessibility feature, many companies may require this when creating forms.

### 2. Lively up your buttons!
The box-shadow can do a lot more then simply make a typical shadow on an element. Try this out for some fun with buttons just using box shadow.

1. The key takeaway here is to note the 4th box-shadow value which is the *spread* or *distance* of the shadow. I.e, { box-shadow: 0px 0px 0px **4px** pink; }
2. We can also chain multiple box-shadow’s to the same element!

[![Styled Button Example](https://www.robhitt.com/blog/four-css-tricks/images/better-button.png)](https://youtu.be/O1KiuqPI8Y4)

```css
.btn {
  padding: 1em 1.5em;
  background-color: #F012BE;
  color: #FFF;
  border-radius: 5px;
  text-decoration: none;
  transition: all 300ms;
}
/*
- For this desired effect we don't include blurr, only the spread.
- In the example below we chain 2 box-shadow properties together.
- 1st box-shadow is solid white 2px box around the entire element.
- 2nd box-shadow starts the pink box after the 2 white pixels
*/
.btn:hover {
  box-shadow: 0px 0px 0px 2px #fff, 0px 0px 0px 6px #F012BE;
}
```

### 3. Simple (yet fun) Animation
I haven't dug too deep into animations in CSS so I wanted to start figuring out how keyframes and animating work.

[![Basketball](https://www.robhitt.com/blog/four-css-tricks/images/animated-ball.png)](https://youtu.be/QjpY2ADP-N8)

```css
.container {
  width: 285px;
  height: 420px;
  margin: 0 auto;
}
/* Notice in the annimation property it calls 'ball-float' which is defined beneath .ball-container the @keyframes selector */
.ball-container {
  position: relative;
  background-image: url(../images/basketball.png);
  width: 285px;
  height: 285px;
  top: 0px;
  animation: ball-float linear 3s infinite;
}
/* This moves the ball down 100px closer to the shadow */
@keyframes ball-float {
  50% { top: 100px } /* can use to and from instead of 50%/100% */
  100% { top: 0px }
}
/* Use the shadow-react keyframe you declared below */
.shadow {
  position: relative;
  height: 16px;
  background: #999;
  opacity: 0.3;
  border-radius: 100%;
  margin: 0;
  top: 100px;
  animation: shadow-react linear 3s infinite;
}
/* Here we shrink and darkening the shadow as the ball falls */
@keyframes shadow-react {
  50% { margin: 0px 20% 0px 20%; opacity: 0.7; }
  100% { margin: 0px 0px 0px 0px; opacity: 0.1; }
}
```

Have any new CSS tricks I need to know? Please send me a pull request here adding yours: https://github.com/robhitt/four-css-tricks  

You can check these all out live right here: https://www.robhitt.com/blog/four-css-tricks/
