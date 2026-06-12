---
title: "Boxee is slow on mythbuntu"
date: 2010-03-29
forum: Mythbuntu
---

### Post by dibuntux on 2010-03-29
Hi guys, I recently added a button to myth main menu to launch Boxee. It runs, but is terribly slow in loading apps and files.
For example, I load shoutcast and it takes forever to display a list of station; you select one and it takes forever to display the play option; and it takes forever from the actual press on play to actually play the file, which then plays fine.

Boxee is also slow in navigating with cursor from option to option. I even tried stopping front end and back end, same results.

The strange is that I have Boxee on another PC on my home net running Ubuntu 9.10 AMD64 and it works fast on everything; yes it is the exact same boxee version.

Any ideas? TIA

Mythbuntu 9.10 AMD64
Gigabyte GA-M720 2GB DDR2-800
Athlon X2 4800+
Nvidia 9400GT 1GB
WD Sata2 CaviarGreen
Skystar 2 DVB-s
Nova T-500 dual DVB-t

---

### Post by azmyth on 2010-03-29
Which Boxee? Alpha works well. I could never get Beta to work properly on 64 bit. That was a few months ago that I tried.

---

### Post by dibuntux on 2010-03-30
Yes, it is Boxee beta 0.9.20.10710 for Ubuntu 9.10 AMD64 (the latest). Which indeed works well on Ubuntu 9.10 AMD64, but not on Mythbuntu 9.10 AMD64 - same network config...

So I guess I just have to wait for the new version? TIA

---

### Post by Lepy on 2010-03-30
Boxee on 64bit has given me trouble since the first alpha was released, even though there wasn't an actual 64bit build available! 

I recently upgraded my main front/back to 64bit (running myth 9.10) and noticed slowness. I don't notice navigation slowness, just  app/icon loading.

With your recommendation, I just installed 0.9.20.10710 (using the same .deb used when installing on myth 9.10) on a computer with vanilla 9.10 AMD64, and the slowness is not there. I'm interested in what could be causing this. Too bad I want boxee working 100% on my myth machines!

---

### Post by azmyth on 2010-03-30
Interesting. I figured if it was slow on MB it would be slow on Ubuntu. My other Ubuntu comp is a 386 so I couldn't test.

BTW, there's a script to install the 386 Alpha Boxee deb on a 64 bit computer.

---

### Post by derrick81787 on 2010-05-27
The menu slowness can be fixed.  When I first installed Boxee, it would take 3-5 seconds just to move the cursor on the menu.  I think it is a video card issue.  To fix it:

1. Open ~/.config/boxee/guisettings.xml in a text editor.

2. Search for the line:
```
<vsync>2</vsync>
```
Note the **vsync**, not **sync**.  These are two different lines.

3. Change the 2 to a 0 and save the file.

After that, if you restart Boxee, it should work.  It did for me anyway.  I remember being told that it could possibly lower the quality of video playback, but I don't know.  You can at least try it because it fixed it for me.

- Derrick

---

### Post by Lepy on 2010-05-27
The slowness I was experiencing did not seem related to vsync, as changing it did not resolve the problem.

I upgraded boxee to version 0.9.21.11487 when it was released, and I have no longer experience any app/icon loading slowness. In fact, it might be the best boxee build I have had the pleasure of using.

---

### Post by derrick81787 on 2010-05-28
I also found that sometimes it helps with speed to run Boxee as root.  I haven't figured out why, though.

---

### Post by tgm4883 on 2010-05-28
> **derrick81787 said:**
> I also found that sometimes it helps with speed to run Boxee as root.  I haven't figured out why, though.

That just seems like a very bad idea

---

### Post by derrick81787 on 2010-05-28
> **tgm4883 said:**
> That just seems like a very bad idea

I agree that it doesn't sound like a good idea.  I just saw online that someone else had done it, and so while I was trying many things, I tried that.  Now, I'm trying to figure out why this would speed it up.  Maybe there are permissions issues or something.

- Derrick

---

