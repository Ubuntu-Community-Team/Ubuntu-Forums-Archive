---
title: "Conky"
date: 2008-08-08
forum: Multimedia Software
---

### Post by trebllaw on 2008-08-08
Quick Question: How do i embod conky into the desktop like that on wolvix? because when i run conky it just run with a window and i can move it. what i want to accomplish is to embed it to the desktop and everytime i start ubuntu it also starts..

---

### Post by easybake on 2008-08-08
> **trebllaw said:**
> Quick Question: How do i embod conky into the desktop like that on wolvix? because when i run conky it just run with a window and i can move it. what i want to accomplish is to embed it to the desktop and everytime i start ubuntu it also starts..

put above TEXT ```
own_window_type override
```

---

### Post by trebllaw on 2008-08-08
uhmm, cant understand where to put the code you said..

could you please elaborate more on how to do it? do i open a terminal, etc...

---

### Post by easybake on 2008-08-08
> **trebllaw said:**
> uhmm, cant understand where to put the code you said..

could you please elaborate more on how to do it? do i open a terminal, etc...

Sorry, open terminal and type ```
gedit .conkyrc
```
You should see a bunch of text that is the variables and configuration settings for producing your conky. This is where you can edit your conky.

If you scroll down you should see an area that says "TEXT". The items below it are the conky variables. The items above it are the Configuration settings. Somewhere above TEXT, you should find some listings that start own_window... find the one that says _own_window_type _ and change it to the code I wrote in the 1st response.

---

### Post by trebllaw on 2008-08-08
and is there a setting there to change the default location on where to start conky? i mean the x and y axis where conky would appear?

---

### Post by easybake on 2008-08-08
> **trebllaw said:**
> and is there a setting there to change the default location on where to start conky? i mean the x and y axis where conky would appear?

It should have if you got a decent conkyrc from somewhere. There are 2 things you have to know. You can start by inputting where you want conky located on the screen. The best way to do this is by copying this into your conkyrc above TEXT if it isn't already there.
```

#alignment top_left
#alignment top_right
#alignment bottom_left
#alignment bottom_right

```
Any line that is started by a # conky will ignore it. So simply delete the # for the area you want conky to start at.

Doing this lines up Conky on the exact edges of your screen. So you probably want to create a gap inbetween conky and the edge of your screen. Add this above TEXT. The values are in pixels you can change them how you see fit.
```

gap_x 10
gap_y 10

```

---

### Post by easybake on 2008-08-08
> **trebllaw said:**
>  everytime i start ubuntu it also starts..

Go into **System>Preferences>Sessions** 
Click +Add
**For Name** Conky
**For Command** Conky

You may run into a problem if you use Compiz as your window manager and it would require you to create a sleep script to launch Conky. If this happens:

**First delete the Conky entry in the Sessions menu.**
[B]
Then In Terminal type[/B]
```
gedit conkystart
```
Paste this in the text editor
```
#!/bin/bash
sleep 20 &&
conky
```
Save and Close.
**In Terminal type;**
```
sudo chmod a+x conkystart
```
enter your password when asked.

**Go into System>Preferences>Sessions**
**Click +Add**
**For Name** ConkyStart
**For Command** ./conkystart

---

