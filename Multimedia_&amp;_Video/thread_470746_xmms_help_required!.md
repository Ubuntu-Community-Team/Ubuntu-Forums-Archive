---
title: "xmms help required!"
date: 2007-06-11
forum: Multimedia &amp; Video
---

### Post by napster86 on 2007-06-11
hey i installed xmms from add/remove from Application menu..but the menus on right clickin and open/add and all dialog boxes does not show text on the buttons and menus only shortcut keys is displayed but not the text..i hope the image provides better understanding..
[IMG]http://img19.imagevenue.com/loc763/th_72066_sc1_122_763lo.jpeg[/IMG]
[IMG]http://img140.imagevenue.com/loc403/th_72068_sc2_122_403lo.jpeg[/IMG]

---

### Post by napster86 on 2007-06-11
hey guys how to sort out da problemo...

---

### Post by Chappy7777 on 2007-06-11
I have XMMS on Dapper and it works fine. I installed it thru Synaptic, however, I am not sure that this matters. 

What are you clicking on. I see you have it skinned. Did you try the Options button in the upper left hand corner? That is the main button, tho you will get menus and other options if you click on the letters of OASIS to the left of the time remaining box. Click on the O, A, S, I, S. Each one will give you a different options.

Best bet is to click on the main Option "box" in upper left corner. It is exactly the same as in Winamp. In your screen shot you have the playlist editor on top of the main box. Click to the upper left of the grey box you show on top of the Multimedia System. 

What exactly are you looking for? I guess the Option box with preferences. That is what should pop up when you click where I said. Try clicking with the left mouse button. That may be all you are doing wrong.

I don't know what else to say other than if this doesn't work, give more info of exactly where you clicked and what you are looking for. I am sure there is a help file in there someplace. Keep patient, if this doesn't work, someone else may be able to explain it better. But if you do as I said, left click on the tiny button in the very upper left hand corner of the main XMMS box that has the name of what you are hearing scrolling across the window, you should get what you need. A complete list of all options and preferences.

---

### Post by napster86 on 2007-06-12
I have not skinned my xmms i just installed and launched it...
Hey There is no description of what L does for example :-the menu should show like

Open L
like that..

I hope this will make it clear...
I have attatched the load file dialog box..
 How to figure out wht action it does and  same problem existing with auadcity which i installed @ the time of posting...

U can see that there is no text written on the buttons..

---

### Post by ubu-for on 2007-06-12
> **napster86 said:**
> hey guys how to sort out da problemo...

Maybe you have a problem with the Nvidia/ATI driver?

---

### Post by napster86 on 2007-06-12
im having intel chipset motherboard a lowend pc and no dont even think of me havin nvidia/ati driver for everyother appz its workin fine..

---

### Post by napster86 on 2007-06-12
hey i found out what the cause of the problem can u guys help me solivng that

[B][I]xyz@xyz-desktop:~$ xmms
Message: device: default

** WARNING **: Failed to open font: "l".
[/I][/B]

hey guys u can see its font problem please help

---

### Post by tgalati4 on 2007-06-12
It looks like you have a language localization problem.  Go into your preferences and make sure your native language is selected.  It's possible that you have a language installed that XMMS does not have hooks for.

---

### Post by napster86 on 2007-06-14
hey u guys deviating me from issue and theres no such lang localisation pbr 

ok lemme put it this way does xmms require gtk+1.2 version to be installed.

---

### Post by tgalati4 on 2007-06-14
What Language do you have set in Gnome System-->Preferences-->Language?

---

### Post by napster86 on 2007-06-14
hey thanks trying to help me sort out my probs tgalati4. But hey tgalati4 EUREKA i resolved this issue lemme explain what i did:-

1.Downloaded the gtklib1.2 from
[http://packages.debian.org/unstable/oldlibs/libgtk1.2-common]("http://packages.debian.org/unstable/oldlibs/libgtk1.2-common")
2.When installing it prompted that its already installed but gave an option of Reinstallin,Did the reinstallation.{Never say die kind of attitude :) }
3.Alt-F2>xmms>EUREKA>Success Now u can see the but obvious difference. between the first screenshot and the last below.

[IMG]http://img175.imagevenue.com/loc520/th_46254_Screenshot-XMMS_-_1._Mithoon_8_Shilpa_Rao_-_Woh_Ajnabee_452078_122_520lo.jpeg[/IMG]

Hey once Again i thank all you gr8 kind hearted guys of the forum.

---

### Post by tgalati4 on 2007-06-14
Sounds like you had a busted Gnome Toolkit.  It's rare but it happens.  By reinstalling you fixed the problem yourself.  That's good news.  What's troubling is how did GTK break in the first place?

If your disk drive is more than a couple of years old then it's time to put SMART monitoring on it.

sudo apt-get install smartmontools
man smartd

to get started.  You might have a failing drive.  I can't imagine why GTK would break unless you added libraries or built programs manually and that messed up your GTK  library.

Congrats again.  We're glad to help you help yourself.

---

### Post by cnu on 2007-06-21
I too have got the same problem on my fresh install of Feisty. Even reinstalling the libgtk1.2-common package doesn't solve it.
Any solutions?

---

