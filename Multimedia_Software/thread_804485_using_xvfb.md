---
title: "using xvfb"
date: 2008-05-23
forum: Multimedia Software
---

### Post by napsy on 2008-05-23
Hello.

I'm creating a virtual display using Xvfb as screen .nr :1. using the command:
> Xvfb :1 -ac -screen 1 800x600x24

Then I start gcalctool and redirect the rendering to screen :1
> gcalctool --display :1

Is there now a way to create a second screen using the same :1 display without creating a new one? So that I could still use display :1 but on a different screen to start another program on it?

Greets,
Luka

---

### Post by jannol on 2008-06-01
Xvfb :1 -ac -screen 1 800x600x24 -screen 2 800x600x24

gcalctool --display :1.1

gedit --display 1.2

---

