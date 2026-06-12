---
title: "copy/paste from terminal wndow to another window"
date: 2011-03-01
forum: Networking &amp; Wireless
---

### Post by Neurocam on 2011-03-01
Greetings,
I have problem with internet connection on my Ubuntu, but the major problem is that i can't copy the message from my terminal while I type:ifgonfig and paste it here to show you what is the problem.
Thank you in advance for helping me
Kind Regards

---

### Post by spiky001 on 2011-03-01
Do you select the type then right click and copy?

---

### Post by chili555 on 2011-03-01
> i can't copy the message from my terminal while I type:ifgonfig Actually, you can. Highlight the text, right-click it and select 'copy.' Please see attached.

I hope you really type ifconfig.

---

### Post by Animal X on 2011-03-01
or if it really is that difficult, why not-
> ifconfig > ~/Desktop/ifconfig.txt

---

### Post by Neurocam on 2011-03-02
Dear All, Thank you,
 
I think I haven't explained properly my problem.
I have installed **virtualbox+ubuntu 10.10** on a **windows 7** HOST operating system.
I could connect to the **internet** with **virtualbox+ubuntu** but I don't know what has happened to it cause it doesn't connect to the** net** anymore.
By **googling** I found that I have to type **'ifconfig'** to find my connection problem, but Unfortunately I can't paste the message from my terminal to this window:(
If you tell me which part of it can be important I can write it by myself on this window.
Thank you again

---

### Post by Random_Dude on 2011-03-02
> **Neurocam said:**
> Dear All, Thank you,
 
I think I haven't explained properly my problem.
I have installed **virtualbox+ubuntu 10.10** on a **windows 7** HOST operating system.
I could connect to the **internet** with **virtualbox+ubuntu** but I don't know what has happened to it cause it doesn't connect to the** net** anymore.
By **googling** I found that I have to type **'ifconfig'** to find my connection problem, but Unfortunately I can't paste the message from my terminal to this window:(
If you tell me which part of it can be important I can write it by myself on this window.
Thank you again

1 Paste it to a .txt file;
2 copy file to pen;
3 open pen in windows;
4 paste text to where you want;
5 ???
6 PROFIT

---

### Post by Neurocam on 2011-03-02
Dear Random_Dude,
 
Thank you for your reply. I am sorry I am too newbie to help you, but I didn't understand what is copying a text file to pen? what is a pen?
Generally is it possible to copy something from a virtual box to another operating system?

---

### Post by malspa on 2011-03-02
> **Neurocam said:**
> Dear Random_Dude,
 
Thank you for your reply. I am sorry I am too newbie to help you, but I didn't understand what is copying a text file to pen? what is a pen?

I think he means flash drive.

---

### Post by mcduck on 2011-03-02
There are several ways to cupy/paste with terminals:

1. Right-click and select copy or paste from the menu

2. Shift-Ctrl-c and Shift-Ctrl-v

3. Highlight what you want to copy, and middle click where you want to paste it. This works in pretty much every Linux application.

I prefer the last option, much less work than any menu option or keyboard shortcut would be.

The "normal" ctrl-c and ctrl-v shortcuts don't work because they already have a completely different purpose on command line interfaces.

---

### Post by Random_Dude on 2011-03-02
> **malspa said:**
> I think he means flash drive.
Yes, that's it.

You can try to copy what appears in the terminal (by pressing Ctrl+Shift+c) to a txt file.
If you can open flash drives in the virtualbox, then you should be able to retrieve the txt file to Windows 7.

Cheers :cool:

---

### Post by ursubaloo on 2011-03-04
Hi, don't know if this is the right place to ask this or if it's been answered elsewhere... but is there any way to invert what Ctrl+C and Ctrl+Shift+C does in the terminal, same with Ctrl+V and Ctrl+Shift+V.  ie. I want ctrl+c to always copy, and ctrl+shift+c to send the break signal, similarly i want ctrl+v to always paste and ctrl+shift+v to send whatever the ctrl+v normally sends to the terminal.  Thanks for your help.

---

### Post by Random_Dude on 2011-03-05
On the Edit menu on top, you got one option that let's you define the keys.

Hope it helps.

Cheers :cool:

---

### Post by ursubaloo on 2011-03-08
> **Random_Dude said:**
> On the Edit menu on top, you got one option that let's you define the keys.

Hope it helps.

Cheers :cool:

Right, I saw that. I can change copy to "ctrl+c" and paste to "ctrl+v" ,  but then I lose the ability to send break to the terminal. I don't want  to just override what normal ctrl+c does in the terminal since I still  need to tell it to break from time to time. 

That edit menu doesn't let you define new shortcuts from what I can  tell. Is there any other place I can get this to work (I looked in  System->Preferences->Keyboard Shortcuts already and didn't find  anything.)

Thanks

---

