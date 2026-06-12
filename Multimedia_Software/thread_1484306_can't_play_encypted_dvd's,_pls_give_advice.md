---
title: "can't play encypted dvd's, pls give advice"
date: 2010-05-15
forum: Multimedia Software
---

### Post by viktor03 on 2010-05-15
dear all,  i've tried to play a dvd with mplayer, totem, vlc and kaffeine. and they all don't work. the problem is only with recent dvd's, with new codecs i guess. with kaffeine i get an error-message that i need libdvdcss and then need to install this on commandline. already did that, and rebooted, still same message vlc gives an error-message simply saying it's unable to open  any advice is much appreciated  viktor03

---

### Post by jerome1232 on 2010-05-15
Did you add the medibuntu repositories and install libdvdcss2? I was under the impression that it's not available in the standard repositories.

---

### Post by Jonners59 on 2010-05-15
> **jerome1232 said:**
> Did you add the medibuntu repositories and install libdvdcss2? I was under the impression that it's not available in the standard repositories.

I am having the same trouble.  I can't play any DVDs or burn ISO....  since the upgrade to 10.4.  I tried the old fix as used in 9.10 with the change of source, which included the libdvdcss2 and others, but that failed to install.  I then tried through Synaptics and that had amongst loads of other upgrades (29) inc libdvdcss2, but it still does not work using VLC, Movie Player or Dragon.

It still does not work.I am now installing every component of Dragon, Movie player, Totem, VLC and Kaffeine.

I do not understand how these can be marketed as DVD players when they never play DVDs without masses of Terminal work

---

### Post by viktor03 on 2010-05-16
@jerome1232: thnks for the reply, i hadn't installed libdvdcss2, but it appears it isn't necessary. i actually was a little dumb right there, after trying to fix it by installing new media players i installed the libdvdcss but forgot i had taken out the disc. :-| I worked fine after just installing libdvdcss.  @jonners59: i'm more thinking out loud here, but if both iso and dvd doesn't work. perhaps your device doesn't get mounted? or maybe there is a problem with the driver? are there other things not working like audio cd? by the way, the reason for all the terminal work, which isn't that much if you know what to do (don't worry, spend an hour on it myself), is that the newer codecs are proprietary if you think it's a problem with the codec, try playing an old dvd (if you have one), that should work without installing libdvdcss or anything (if you dvd works)

---

### Post by evilwonka on 2010-05-16
i dont know how to install libdvdcss thru terminal im new to this os

---

### Post by axel206 on 2010-05-16
Try this:

[http://www.my-guides.net/en/guides/linux/193-ubuntu-lucid-lynx-1004-post-installation-guide#dvd-playback](http://www.my-guides.net/en/guides/linux/193-ubuntu-lucid-lynx-1004-post-installation-guide#dvd-playback)

---

### Post by Jonners59 on 2010-05-16
> **viktor03 said:**
> @jerome1232: @jonners59: i'm more thinking out loud here, but if both iso and dvd doesn't work. perhaps your device doesn't get mounted? or maybe there is a problem with the driver? are there other things not working like audio cd? by the way, the reason for all the terminal work, which isn't that much if you know what to do (don't worry, spend an hour on it myself), is that the newer codecs are proprietary if you think it's a problem with the codec, try playing an old dvd (if you have one), that should work without installing libdvdcss or anything (if you dvd works)

I can load and read CDs...  This is a common issue on Ubuntu and there are lots of articles from previous versions 8.4 and 9.10 that give command line to get it up and running.  I had this on 5 machines when I set up the above on them last year.  So useful I kept a soft copy of the stages...

Does not work this time.  That said, maybe my player is faulty.  I have to replace one of the drives in one of the machines ( have 2 per machine) so I can test then, but it does not answer why it has not worked in the past and on so many machines of various makes and age until the terminal stages mentioned are carried out.  And once it did get up and running, why it stopped as soon as I upgraded to 10.4.

---

### Post by jerome1232 on 2010-05-16
?

You don't **need** to do anything with a command line to get encrypted dvd's working.

You have to add medibuntu repositories, then install libdvdcss2, that's all.

You can use System->Administration->Software Sources to add additional repositories. You can use Synaptic Package Manger to then install libdvdcss2.

Medibuntu has a little how-to in which they give you a one line terminal command that will add their repository (because let's face it, it's easier to copy and paste that one command rather than follow a gui tutorial on what to click and where)

You can find that tutorial [here]("https://help.ubuntu.com/community/Medibuntu")

You may also need to install the ubuntu-restricted-extras package, which provides all of the codecs you should ever dream of using. Look for it in synaptic package manager.

I hope that helps you out.

---

### Post by Jonners59 on 2010-05-17
> **jerome1232 said:**
> ?

You don't **need** to do anything with a command line to get encrypted dvd's working.

You have to add medibuntu repositories, then install libdvdcss2, that's all.

You can use System->Administration->Software Sources to add additional repositories. You can use Synaptic Package Manger to then install libdvdcss2.

Medibuntu has a little how-to in which they give you a one line terminal command that will add their repository (because let's face it, it's easier to copy and paste that one command rather than follow a gui tutorial on what to click and where)

You can find that tutorial [here]("https://help.ubuntu.com/community/Medibuntu")

You may also need to install the ubuntu-restricted-extras package, which provides all of the codecs you should ever dream of using. Look for it in synaptic package manager.

I hope that helps you out.
Did that...  did not work, and now when I try to open a folder or drive it tries to open with VNC

I am going to buy a new DVD, not that I think there is anything wrong with it, as I can open DVDs with files, and other apps, but just not VOB

---

### Post by Jonners59 on 2010-05-20
OK.  I have now bought a nice new internal DVD drive.  It still does not play VOB files.

Before I had it play the copy right file, but then stop and not be able to play the film.  Now, having installed the recommendations below.  It plays nothing in any of the Player Apps.

I can, as before, browse the DVD.

Also, as stated, since implementing the recommendations opens VNC whenever I try and open a directory either on the PC, a removable media or on a different PC on the LAN, which is b***dy annoying!!!!!

[COLOR=Red]Can anyone help me, please?[/COLOR]

---

### Post by Jonners59 on 2010-05-20
Agh...  Just started to work.....

Now, how do we stop VNC opening directories when they are selected... [COLOR=Red] Anyone help, please?[/COLOR]

---

### Post by viktor03 on 2010-05-20
tried opening them with right-click and selecting what you want to use?

---

### Post by Jonners59 on 2010-05-20
> **viktor03 said:**
> tried opening them with right-click and selecting what you want to use?
Of course.  Not only does it just try and open by VNC, but if I select from Places there is no such option...  The ONLY way to open folders, media, directories, is to select Place, Computer, then select the Hard drive (if it is not on the LAN) and then open in the normal way (double click).

This all happened after I followed the instructions below.

---

### Post by Jonners59 on 2010-05-23
[color=red]any help please?????????[/color]

---

### Post by jerome1232 on 2010-05-24
what is the default file browser in xubuntu?

open a terminal and run your file browser, right click a folder and make sure it it selected as the default program to open folders.

Nothing in my instructions would've set vlc to be the default program to open folders, in fact it had nothing to do with vlc or the file browser. Not sure how that happened.

---

### Post by Jonners59 on 2010-05-25
> **jerome1232 said:**
> what is the default file browser in xubuntu?

open a terminal and run your file browser, right click a folder and make sure it it selected as the default program to open folders.

Nothing in my instructions would've set vlc to be the default program to open folders, in fact it had nothing to do with vlc or the file browser. Not sure how that happened.

It must have somehow tampered in some way...  Anyway, what I did was:
The Hard Drives I could right click I noticed it still said open with File Browser, so I selected "Properties" and "Open With".  In there I noticed it was set to VLC, so I changed back to File Browser.

The others, mostly Bookmarks, I just deleted them and re created them.  They all (bar two, who seemed to have now created security access requirements?) work now.

I should have done this before.  I'll close this off.

---

