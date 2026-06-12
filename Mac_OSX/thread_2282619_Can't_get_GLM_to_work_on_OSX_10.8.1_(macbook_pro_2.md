---
title: "Can't get GLM to work on OSX 10.8.1 (macbook pro 2006)"
date: 2015-06-15
forum: Mac OSX
---

### Post by barkerson on 2015-06-15
Tried to get help >[here]("http://stackoverflow.com/questions/30785786/glm-errors-when-trying-to-compile-on-osx-10-8")< first.

So basically I got OpenGL, GLEW and GLFW3 to work on my macbook pro I got for free. Where the problems began is when I tried to add the GLM header library (inside the include folder).

This was the errors in 'func_trigonometric.inl' from the GLM library.
```

/usr/local/includ... 165    current parser token 'if'
/usr/local/includ... 37     parsing namespace 'glm'
/usr/local/includ... 160    parsing function body 'tanh'
/usr/local/includ... 160    in compound statement ('{}')
                            note: diagnostic msg: Error generating preprocessed source(s).

```

I'm using Code::Blocks 12.13 and this is the only problem I've encountered so far, my code works on windows and linux with no problems too.

Help much appreciated.

---

