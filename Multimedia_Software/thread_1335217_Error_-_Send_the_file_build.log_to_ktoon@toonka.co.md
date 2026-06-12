---
title: "Error - Send the file build.log to ktoon@toonka.com"
date: 2009-11-23
forum: Multimedia Software
---

### Post by Distriker on 2009-11-23
Hello, I have a problem when I go to install KToon through the terminal (I want install by terminal).

I have got the QT4 and the QT4-qmake yet. After, in the terminal I write this:

```
./configure [--enable-ktoonstyle] [--enable-kinas]
```Well, this pass is easy. Then, I write this (and here it's the error):

```
./build.sh --prefix [prefix]
```I click, yes, yes, yes and yes, but in the end, say this:

```
 *  Error
Send the file build.log to ktoon@toonka.com
```The all process is this:

```
distriker@Distriker:~/Escritorio/ktoon0.8_beta$ ./build.sh --prefix [prefix]
 *  Using Qt: 4.5.0
 *  Do you wants compile opengl version (y/n)?  y
 *  Do you wants debug support (y/n)?  y

 *  ###################################
 *  -> Using OpenGL version
 *  -> Using DEBUG support
 *  ###################################

 *  This is right (y/n)?  y
Wait a moment...........................................................
 *  Do you wants clean the project (y/n)?  y
 *  Cleaning...
 *  Compiling KToon 0.8beta-svn...
 *  Go for a coffee cup ;)
.
 *  Error
Send the file build.log to ktoon@toonka.com
.
distriker@Distriker:~/Escritorio/ktoon0.8_beta$ ./build.sh --prefix [prefix]
 *  Using Qt: 4.5.0
 *  Do you wants compile opengl version (y/n)?  y
 *  Do you wants debug support (y/n)?  y

 *  ###################################
 *  -> Using OpenGL version
 *  -> Using DEBUG support
 *  ###################################

 *  This is right (y/n)?  y
Wait a moment...........................................................
 *  Do you wants clean the project (y/n)?  n
 *  Compiling KToon 0.8beta-svn...
 *  Go for a coffee cup ;)
.
 *  Error
Send the file build.log to ktoon@toonka.com
.

```What do you think about my problem?

Greetings.

---

