---
title: "Open Office problem on OsX"
date: 2007-04-12
forum: Mac OSX
---

### Post by seshomaru samma on 2007-04-12
My friend just bought a Mac Book (Tiger) and asked me to help her install Open Office on it
I never used a Mac before , but I know a little about computers while my friend is still not sure what is the difference between downloading and installing.
I downloaded OO for Mac and some X environment it needs , but when I run the X environment the installer claimed that a newer programme is already installed . I then installed OO and everything seemed quite smooth. A windows appeared which asked me to drag the OO icon into 'applications' . I did that and then dragged it into the dock. But whenever I click the OO icon i get a screen asking if I want to use the system fonts ,if I choose yes , nothing happens. If I choose no , nothing happens.
I remember reading a post here by super member aysiu saying he can use the bash terminal in osx , so i run the command top but open office wasn't there. I tried to run OO from the terminal but couldn't find the exact command. I couldn't locate its directory as well, cause the locate command didn't work.
Anyway , does anyone know how to solve this problem?

---

### Post by TheWizzard on 2007-04-12
try this command:
oowriter

---

### Post by oskarloko on 2007-04-12
Just try

[http://www.neooffice.org/neojava/es/index.php](http://www.neooffice.org/neojava/es/index.php)

---

### Post by seshomaru samma on 2007-04-13
the command oowriter didnt work
im downloading neooffice as we speak
but why is downloading things in osx so slow?
i tried to download firefox and stopped after a few hours
my friend said they use bit torrent for downloading but isnt there a simpler way ?

EDIT-installed NeoOffice -looks very cool . Thanks for the tip!

---

### Post by TheWizzard on 2007-04-13
> **seshomaru samma said:**
> the command oowriter didnt work


looks like it wasn't properly installed then. 

good luck with neooffice

---

### Post by ThinkBuntu on 2007-04-13
NeoOffice for Mac is as good as OpenOffice for Linux. Development of OpenOffice for Mac stopped a year ago, so...

---

### Post by TheWizzard on 2007-04-13
> **ThinkBuntu said:**
> Development of OpenOffice for Mac stopped a year ago, so...

where did you get this information from? looks like OOo 2.2 is ported for mac: 
[http://porting.openoffice.org/mac/](http://porting.openoffice.org/mac/)

---

### Post by rccharles on 2007-04-20
> **seshomaru samma said:**
> 
I downloaded OO for Mac and some X environment it needs , but when I run the X environment the installer claimed that a newer programme is already installed . 

Where did you get the X environment?  On the Mac, folks refer to X as X11.

Apple has created there own version of X11.  You can download it from the Apple web site or load it off of the installation disk.

The instruction are minimal:
[http://developer.apple.com/opensource/tools/runningx11.html](http://developer.apple.com/opensource/tools/runningx11.html)

And you can download it:
[http://www.apple.com/support/downloads/x11formacosx.html](http://www.apple.com/support/downloads/x11formacosx.html)



Here is some old help on installing:
[http://www.macdevcenter.com/pub/a/mac/2003/02/07/x11.html](http://www.macdevcenter.com/pub/a/mac/2003/02/07/x11.html) 

---------

As for the slow download speed, you can try Activity Monitor then Network:
harddrive > Applications > Utilities > Activity Monitor

---------

The terminal command whereis will find things.

The terminal command open-x11 will start x11 applications.

---------

Of course, neoOffice is probably better in your situation.

Robert

---

### Post by seshomaru samma on 2007-04-23
Thanks 
I installed neo-office and she was happy....

I tried to install Firefox for her but downloading it took hours and I gave up. It seems like most downloads for OSX go through torrent clients . I just gave up, she can use Safari anyway...

---

### Post by Alfa989 on 2007-04-23
> **seshomaru samma said:**
> Thanks 
I installed neo-office and she was happy....

I tried to install Firefox for her but downloading it took hours and I gave up. It seems like most downloads for OSX go through torrent clients . I just gave up, she can use Safari anyway...

Must be something weird happening with her network or even with OS X itself... I suggest repairing permissions...

"It seems like most downloads for OSX go through torrent clients"
What do you mean?

---

### Post by rccharles on 2007-04-23
> **seshomaru samma said:**
> 
I tried to install Firefox for her but downloading it took hours and I gave up. It seems like most downloads for OSX go through torrent clients . I just gave up, she can use Safari anyway...

Firefox is 17.6 meg.  Does she have a modem connection.  Even if you have a 56k modem, some phone lines only let you run at 28.8k. I have never used a torrent client on my Mac.

Robert

---

### Post by the.dark.lord on 2007-04-25
If you downloaded the X11 version of OOo, make sure you have X11 installed.

---

