---
title: "My Windows Borders are Missing!"
date: 2006-07-25
forum: Multimedia &amp; Video
---

### Post by RPG405 on 2006-07-25
Just as the topic says, I am missing my window borders and titlebars. A screenshot of the problem is attached.

Here's how the problem started: I was typing a paper one day, when I accidently made a mistake misspelling an all-caps acronym. Since the acronym was all caps, I had my finger on the SHIFT key as I pressed "Backspace". Unfourtanately, that's the kill sequence for XGL, and I was hence dumped into a blank screen. After a minute of nothing happening, I pressed the reboot button on my machine and rebooted. When I came back, none of my windows had borders. Or titlebars.

I recently installed XGL and Compiz. As you can imagine it is very difficult to manage your windows without titlebars! Help would be greatly appreciated.

---

### Post by JerMe on 2006-07-26
edit:

doh,

```
gnome-window-decorator&
```

---

### Post by ericesque on 2006-07-26
Check the output of 

fglrxinfo


I found that I lost my window borders when I was using mesa instead of proprietary drivers.  You using ATI?

If so, I'll try to find a link to help you out.

---

### Post by RPG405 on 2006-07-26
Hi,

I forgot to mention I am using an nVidia GeForce 6600 GT graphics card with the drivers installed.

The command gnome-window-manager is not found (gasp!)
The command fglrxinfo is not found (gasp!)

---

### Post by jimmygoon on 2006-07-26
> **RPG405 said:**
> Hi,

I forgot to mention I am using an nVidia GeForce 6600 GT graphics card with the drivers installed.

The command gnome-window-manager is not found (gasp!)
The command fglrxinfo is not found (gasp!)

I think the intended command was probably gnome-window-decorator as for the second one, the nvidia card explains it.

Where are you guys install XGL /compiz from. I'm using AIGLX and CGWD from the compiz.net forum (these changes are breaking the window borders everywhere, read up over there for the reasons) and that Shift-Backspace bug has been fixed for like .... forever?!!

---

### Post by jimmygoon on 2006-07-26
Actually, if you are on XGL and using Quinn's packages then simply do this:

```
sudo aptitude update; sudo aptitude install cgwd gcompizthemer gcompizthemer-themes
```

And see if that helps at all... If not, take a look at the red icon in the task tray and right clcik ->Use Metacity... that should help you at least temporarily

---

### Post by ericesque on 2006-07-26
heh.  if you're using Nvidia, it's a good thing that fglrxinfo isn't found.  It's for ATI cards ;)  sorry for the confusion.

@jimmy

I wish I had the time to worry about it, but filtering through those XGL forums is a pain.  It seems like a bunch of mix-and-mash information in a bunch of redundant threads.  Someday there will be an easy tut or install script that doesn't require hours of my time to figure out how to make my windows wobble.  Until then, metacity will do the job for me.

---

### Post by RPG405 on 2006-07-26
I have fixed the problem, although it's not the optimal solution. I simply disabled XGL and Compiz. I agree with ericesque, I can wait :). So for now I have metacity back, and no XGL or Compiz.

Thanks much for all your help! It's people like you that keep Linux alive.

---

### Post by Dubbayoo on 2006-07-26
I had the same issue after trying/failing to get xgl working. I never got any workable solutions so I just reinstalled the whole system.

---

### Post by boban on 2006-08-03
> **RPG405 said:**
> Hi,

I forgot to mention I am using an nVidia GeForce 6600 GT graphics card with the drivers installed.

The command gnome-window-manager is not found (gasp!)
The command fglrxinfo is not found (gasp!)

try:

gnome-window-decorator& :)

---

### Post by JerMe on 2006-08-03
> **boban said:**
> try:

gnome-window-decorator& :)

my bad. ;)  Edited my other post.

---

