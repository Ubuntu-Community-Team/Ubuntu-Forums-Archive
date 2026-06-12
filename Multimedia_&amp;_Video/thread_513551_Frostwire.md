---
title: "Frostwire"
date: 2007-07-30
forum: Multimedia &amp; Video
---

### Post by Chappy7777 on 2007-07-30
NOTE:I just want to say that this problem has been solved, or at least worked around. Thanx to all.

Hi, I just installed Frostwire. The install seems to have gone well. I already installed Java Web Start 1.4. Prior to this install as I was getting a java error every time I tried to open the Frostwire deb file. Now that I have Java installed and working, (at least the Sun Java Control Panel comes up when I click on Apps/Internet/Java) Frostwire is listed under Apps/Internet/Frostwire. However, when I click on it, nothing happens. 

I know this has been asked many times by other UB users, but I can't find an answer that fits my situation. It seems like most folks are having Java related probs as was I prior to installing 1.4

So, Java in place, Frostwire in place, both showing as installed. Java opens and shows me a control panel, but Frostwire does nothing.

BTW, I have Java set to always integrate Java apps into the desktop. In Advanced it says current size is 26KBytes and  /home/ss55/.java/.deployment/javaws/cache    is the app folder. This only tells me where to find it, Whether it set itself up in the right place I can only assume.

Since Frostwire is being seem in Applications/Internet, I am assuming it's installed. Is there something I need to type into terminal? If so....???

Thank you for the help and patience,

---

### Post by Chappy7777 on 2007-07-31
OK, it seems I needed to update java to 1.5  Is this correct? I went to [www.java.com](www.java.com) and downloaded the java for linux bin file. However, I have no idea how to install this new java. I am sure it has to do with the terminal and typing "su", my root password, and then ????

I need some help here, I don't understand why 18 people have looked at my cry for help, and yet no one has taken a try at actually helping me. 

Someone please, I would really like to get Frostwire working, especially now that it's installed, and telling me the problem is: upgrade java 1.4 to 1.5  

If I am going to learn how to use Ubuntu and finally be free from MSoft, I am going to need help learning the commands to do certain things, ie: installing downloaded files.

---

### Post by Chappy7777 on 2007-07-31
For whatever reason this thread is being looked at but not replied to. Either everyone of the 27 viewers has the same problem and is hoping to find their answer here, no one has the answer, or I am asking the wrong people.

If there is someone out there who would answer me if I supplied more info, please ask for it. 

Otherwise, is there somewhere else I can go online where I can find answers to problems w/Ubuntu. 

Tick, tick...

---

### Post by wolfen69 on 2007-07-31
you can install java through synaptic. if it does not show up, you need to enable some repositories. just do a search in synaptic for "JRE".

---

### Post by Chappy7777 on 2007-08-01
thnx Wolfen, I'll post here after I give it a try. I really appreciate your answering me.

---

### Post by rsambuca on 2007-08-01
I had problems for a while as well, but it seems that frostwire liked java 5 better than java6.  I am not using dapper, but I just installed java via synaptic, or you can just type```
sudo apt-get install sun-java5-jre
```

Frostwire looks in certain places for java, and depending on which ubuntu you are using, it could place it somewhere else, so you might have to edit the file which tells frostwire where to look for java (or create a symlink)

After you have installed java1.5, try re-installing frostwire and use a terminal to start it up, so you can see the error messages, if any.  In a terminal, just type ```
frostwire
```
If you get errors, let us know and we can help you out.

---

### Post by MsChevyKat on 2007-08-02
I use gtk-gnutella.  No java needed. :D

---

### Post by Chappy7777 on 2007-08-02
Thnx. I have tried looking for java 5 in synaptic, but I don't see it. I see java 4, Installed.

As for Gtk-Gnutella, can I get that thru Synaptic? 

One of my very BIG!! probs is that I have essentially no idea how to do command lines, or how to use a terminal. I can read my name and understand the info that pops up when I open a terminal or Konsole, but that's about it. How the heck does one go about learning all these commands? Trial and error and doing what's suggested on here? That seems like it would work, but take a long time.

Anyhow, I don't care which program I use, I just want to be able to do what these P2P programs allow. Trade info. Borrow music, etc.

I am gunna go check out these ideas. If I get something working, I'll post it here. Otherwise, please assume I still need help and ideas.

---

### Post by Chappy7777 on 2007-08-02
OK, I found Java 5 in Synaptic, I have found it before. I guess I blanked it from my mind because it says it's a 183 mg download. I am on dialup, So that's like?? 3 weeks, or so. I can't tie up the phone that long.

Sooo... I tried Gnutella thru Synaptic. Did a search, found it. I clicked on "Mark for Installation" and did the download. Now, like Frostwire, it's sitting under Apps/Internet but when I click on it I hear a thunk (UB sounds) but nothing happens. Same as Frostwire.

If I see something under Applications, does that mean it's installed? Should it be working? I get no error message. Just nothing. It sure looked promising.

So, back where I started again. Downloaded and installed by Synaptic, yet no-go.

Ideas out there? I have a dinky video card, but there is no video involved in Frostwire is there, other than drawing the actual program, That is prolly done by RAM anyhow. Since I have enough.

---

### Post by rsambuca on 2007-08-02
Hopefully we can get it up and running for you!

First question: What version of ubuntu are you using?  Dapper like your profile says?

Next, what does it say when you try and run frostwire from a terminal?  To do this, click on "Applications -> Accessories -> Terminal"

When the terminal window opens, at the prompt simply type in```
frostwire
```, and then press enter.  I assume you will get an error message showing in the terminal if frostwire isn't working.  That should help us troubleshoot this.

---

### Post by Chappy7777 on 2007-08-02
> **rsambuca said:**
> Hopefully we can get it up and running for you!

First question: What version of ubuntu are you using?  Dapper like your profile says?

Next, what does it say when you try and run frostwire from a terminal?  To do this, click on "Applications -> Accessories -> Terminal"

When the terminal window opens, at the prompt simply type in```
frostwire
```, and then press enter.  I assume you will get an error message showing in the terminal if frostwire isn't working.  That should help us troubleshoot this.
==============================
Yes, I am using 6.06 I just !! turned my Linux Box off and am on my Windoze machine so I can't tell you about Frostwire in Terminal, but I will do that sooner than later if we don't get a thunderstorm.
Should I try the same thing with Gnutella? 

Thanx alot and I'll get that info up here asap.

---

### Post by cbiere on 2007-08-03
You should definitely start gtk-gnutella from a terminal to see why it doesn't start. There are two likely problems. Either the version is too old so that it won't start anymore if you don't follow the instructions you'll see in the terminal. The other likely issue is your gtk-theme or gnome-theme. Some of these a buggy but these bugs manifest only in certain applications like gtk-gnutella for example which means it'll crash right at startup. Try to change your theme to ClearLooks if you see it crashing. That'll typically fix it. If you use gtk-gnutella 0.96.4 or newer neither should apply to you.

If you can't fetch the newest release through Synaptic, it's also very easy to compile it yourself. The sources can
be downloaded from the SourceForge project site:
 
[https://sourceforge.net/project/showfiles.php?group_id=4467&package_id=4479](https://sourceforge.net/project/showfiles.php?group_id=4467&package_id=4479)

For compiling, just follow these simple instructions:

[https://gtk-gnutella.svn.sourceforge.net/svnroot/gtk-gnutella/trunk/gtk-gnutella/README.Debian](https://gtk-gnutella.svn.sourceforge.net/svnroot/gtk-gnutella/trunk/gtk-gnutella/README.Debian)

You definitely don't need Java for it. Also for using BitTorrent I'd recommend rtorrent.

---

### Post by Chappy7777 on 2007-08-03
I did as suggested and typed  frostwire  into  teminal. The error it came up with is what I already knew. It said I need JRE 1.5, as I only have 1.4  I am hoping to be on hispeed w/in a week or so, and then downloading a 183mg file will be no hassle. But since I now have dialup, I think I'll wait.

I did the same thing with Gtk-gnutella, and got back a long error which essentially said that the version of Gtk-Gnutella that synaptic says is current isn't. The version Synaptic comes up with is 0.96.1 

The error included a work around that supposedly would make Gnutella work just fine. It said to go to the Gtk-Gnutella directory and find the config-gnet file, and change the "ancient-version-force" from
" "  to "gtk-gnutella/0.96.1 (2000-02-22; GTK2; Linux i686"  

I tried this about 10 times and every time, after changing the ancient-version-force by copy and pasting the above fix, I went to Apps/Internet/Gtk-Gnutella and clicked on it. No go. I then went back into the config file and where I had changed the file, it was back to prechange. So, obviously the work around wasn't sticking. I did do a save each time. One time I changed the original to read confi-gnet2.

I haven't been to Gnutella's site to see what they say is the latest/currect version. In Synaptic the installed and the current (before doing a "mark for reinstallation) are the same, 0.96.1

So, seems like I can just wait till I get hi-speed and download the updated version of java, and/or,
see what gnutella says at their site.

---

### Post by rsambuca on 2007-08-03
If you are changing the config file, make sure you press "save" before exiting!  Otherwise, you will not have changed anything.  If it doesn't let you (ie. it says "Read Only"), then just open the file with root permissions before changing it.  To do this, you simply enter```
gksudo gedit <insert path to filename here>
```

---

### Post by Chappy7777 on 2007-08-03
> **cbiere said:**
> You should definitely start gtk-gnutella from a terminal to see why it doesn't start. There are two likely problems. Either the version is too old so that it won't start anymore if you don't follow the instructions you'll see in the terminal. The other likely issue is your gtk-theme or gnome-theme. Some of these a buggy but these bugs manifest only in certain applications like gtk-gnutella for example which means it'll crash right at startup. Try to change your theme to ClearLooks if you see it crashing. That'll typically fix it. If you use gtk-gnutella 0.96.4 or newer neither should apply to you.

If you can't fetch the newest release through Synaptic, it's also very easy to compile it yourself. The sources can
be downloaded from the SourceForge project site:
 
[https://sourceforge.net/project/showfiles.php?group_id=4467&package_id=4479](https://sourceforge.net/project/showfiles.php?group_id=4467&package_id=4479)

For compiling, just follow these simple instructions:

[https://gtk-gnutella.svn.sourceforge.net/svnroot/gtk-gnutella/trunk/gtk-gnutella/README.Debian](https://gtk-gnutella.svn.sourceforge.net/svnroot/gtk-gnutella/trunk/gtk-gnutella/README.Debian)

You definitely don't need Java for it. Also for using BitTorrent I'd recommend rtorrent.
=============================
I went to the top link and am in the process of downloading    	gtk-gnutella-0.96.4.tar.bz2   That is the newest version listed. It was posted on sourceforge in July so it must be the newest.

Can you do me a favor and tell me how to go about installing this file once I have it downloaded?
I am spoiled by Synaptic and Add/Remove, but I can do stuff thru terminal if given the correct steps.

 Since 	gtk-gnutella-0.96.1iss the version that is shown in Synaptic, should I just leave it? My thought is that I should remove it since it is now listed under Application/Internet. My thought is a very uneducated one.

Thnx for the help.

---

### Post by cbiere on 2007-08-03
Just run

  tar -jxvf gtk-gnutella-0.96.4.tar.bz2 && cd gtk-gnutella-0.96.4

then follow the steps in

[https://gtk-gnutella.svn.sourceforge.net/svnroot/gtk-gnutella/trunk/gtk-gnutella/README.Debian](https://gtk-gnutella.svn.sourceforge.net/svnroot/gtk-gnutella/trunk/gtk-gnutella/README.Debian)

The indented lines are the commands which you have to execute your shell.

By the way, what you probably didn't do when you changed the value for ancient_version_force is removing the hash mark (#) in front of the line which means it's commented out and ignored. So if you retry that and remove the # too, it should work. This version is really outdated though and you'll just get a lot of spam besides missing any improvements and bugfixes mentioned in the release history.

---

### Post by Chappy7777 on 2007-08-04
bump

---

### Post by rsambuca on 2007-08-04
If you follow cbiere's last post, you should be good to go.

---

### Post by Chappy7777 on 2007-08-05
Problem solved! Thanks to all who gave me the ideas that enabled me to take a guess at the cure to getting Gtk-Gnutella working. I had already installed 7.04 on a small HD, but I wasn't using it because of troubles connecting to the net. Yesterday I solved that problem, and went into Feisty's Synaptic and found that a much newer version of Gnutella came with 7.04 than I had in 6.06 after doing an update.

Sooo....  I installed 7.04's Gtk-Gnutella 0.94.3 (6.06 could only find 0.94.1). After doing the Synaptic install, I clicked on Apps/Internet/Gtk-Gnutella and it opened up. It looks a little different than Limewire and Frostwire, but after messing around I got an MP3 downloaded and it played just fine on the version of XMMS that Synaptic had waiting.

Since I have spent 6 mos (my life in Linux) putting 6.06 together, I will keep it on the HD it's on. But I am going to keep building 7.04 on it's own HD, and hope that it serves me as well as Dapper has. 

It's very handy having a setup which allows me to slide different HDs in and out of the Dock on my PC. This way if I totally muck up one HD, the others are untouched and still good to go. 

Again thnx, and problem, (sort of) solved,

---

