Rinksprite
==========

[See this in action.](http://rocketnia.github.io/rinksprite/sprite-elisa.html)

This project isn't much, really. It's just a place for me to
experiment with rendering sprites on an HTML canvas. Perhaps it'll
turn into a library someday, but it's not like there aren't plenty of
sprite libraries already. :)

The name "rinksprite" is an homage to Touch Detective episode 3.

### Sprite Rendering

Notably, I use a pretty efficient method to render low-res sprites at
2x or 3x (or Nx) resolution. Here's my secret: First, use `drawImage`
calls to draw each pixel row of the image two or three (or N) times,
making a stretched-out intermediate image. Then do the same for the
columns of that image. This way, we only do (n * (w + h)) `drawImage`
calls, rather than (w * h) `drawRect` calls, and the browser can
optimize this quite a bit better.

What's that, you say? Do just one `drawImage` at the proper scale?
What, and get the browser's friendly image-smoothing technology?

What's that, you say? Just use `imageSmoothingEnabled`? What
newfangled magic is this?!
