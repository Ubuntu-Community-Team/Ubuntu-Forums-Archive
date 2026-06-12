---
title: "Luminance HDR problem"
date: 2012-10-22
forum: Multimedia Software
---

### Post by RobinSchouten on 2012-10-22
Hey all,

I've recently installed Luminance HDR on my 12.10 Ubuntu. As I'm trying to make a full switch to Ubuntu, I need all my programs working correctly. So far I'm really happy with GIMP and Aftershot Pro and I only need a working HDR program to get me going.

Luminance HDR seems great but there's one small problem that keeps me from using it. When I check the box for Auto-align and I press next, I get the following error message: 

> Failed to start external application "align_image_stack".
Please read "Help -> Contents... -> Setting up -> External Tools" for more information.

Checking the help bit doesn't really tell me anything on how to solve this.

Anyone got an idea?
Thanks. :)

---

### Post by RobinSchouten on 2012-10-25
Bump.

---

### Post by Montex on 2012-11-13
Hello,

installing the "hugin-tools" package should solve the issue. It contains the binary for 'align_image_stack'.

Actually it is a packaging bug, for which such package has not been marked as a dependency.

---

