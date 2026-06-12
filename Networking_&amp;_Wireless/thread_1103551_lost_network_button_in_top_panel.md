---
title: "lost network button in top panel"
date: 2009-03-22
forum: Networking &amp; Wireless
---

### Post by john@proficientpc on 2009-03-22
hey yeah ive lost my network button that's suppose to be in the top panel but ive done add to panel and cant find it need help getting it back

---

### Post by dreamingdarkness on 2009-03-22
Hmm
If you lost it just on this boot, try this command from the terminal:

```
ps aux | grep NetworkManager
```

You may find a line like:
```
root      5991  0.0  0.0  14764  2704 ?        Ssl  19:20   0:00 /usr/sbin/NetworkManager
```

If you see that, you need to:
```
sudo kill 5991
```
SO on your terminal it would be:
```
sudo kill <# just to the right of 'root'>
```
Of course, replace the 5991 with whatever the task is on your PC. You will be prompted to enter the user password, which will kill the task.

If you kill it, or if you didn't see it in the ps aux | grep NetworkManager, go to command line and enter:
```
sudo NetworkManager
```

It may or may not prompt you for the password, depending on how your system is set up.
This should run NetworkManager, which brings up the network icon in the top right of your screen.

---

### Post by AR_Kozz on 2009-03-23
You can put the network manager applet back onto the panel by right clicking it and picking "add." Then you will see a menu of about 20 applets that are commonly used on the taskbar, and the network manager should be listed.

Alternatively you can to the menu, to System>Administration>Sessions, and click Add, then type in:

Network Manager

nm-applet --sm-disable

in the first two lines, then

Network Manager applet

in the comment line, if you like. Both achieve basically the same thing.

btw IF anybody knows why the --sm-disable option might not be disabling networking (under Gutsy, x86, in particular) I sure would like to know. Disabling networking with this applet doesn't work in Gutsy on either my pc or my ps3. I can launch Firefox and browse anyway. It has literally  no effect. I just noticed this, and I consider this applet saying networking is "disabled" to be something of a security risk, when it's actually not disabled.

I know I can use sudo in terminal to do the same thing, but it is kind of a drag when I have a lot of things to do... when I'm on a big project I like the terminal stuff to be things I can uparrow and repeat, and I won't do that with root commands. And I ain't putting no root commands on the panel! So what could be trumping session manager to make networking work anyway, even when session manager is told to knock it off? I want my panel switch back.

---

### Post by judeisadawson on 2009-04-06
Hi Guys,
I have a similar problem. I've posted my comments on Launchpad on 06/04/09. I have received some suggestions for the launchpad team. I thought that I could get more suggestions from the Ubuntu Forums. 

The following is the thread:


Posted on 05/04/09) 
Hi All,
I upgraded from Hardy to Intrepid yesterday. I downloaded an alternative installation apps & followed instructions provided in the Ubuntu documentation pages to upgrade the OS.
Everything went well during & after the upgrade.
Today, however, I noticed something wrong. My modem connection was missing from Network Manager at the top-toolbar. So I proceeded to configure the settings once again. I had done it before in hardyu & it was relatively easy with the instructions provided.
Here's the problem. There is no 'Network' selection in the 'Systems - Administrator' dropdown menu. Very strange...

Do I need to reinstall 8.10?

(Posted on 06/04/09)
...Thanks for the info. Unfortunately, I have not solved the problem yet.

Before I continue, here's what I'm trying to do. I'm trying to configure Intrepid to work with my 56k dialup modem connected to my PC via serial connection (don't laugh...). I ran 'wvdial conf' in 'Terminal' and the modem was detected. Moreover, it was working fine in Hardy.

Here's what I've done so far. I right-clicked on the toolbar at the top of the screen & selected 'Add to Panel'. I selected the 'Modem Monitor 2.24.1' apps. The icon appeared on the toolbar.
However, double-clicking it does nothing to it. I then right-clicked the icon & selected 'Properties'. An error message appeared. It said : 'Could not launch network configuration tool. Check that's it's installed in the correct path and that it has the correct permissions.'

Also, I still cannot find the 'Network' tab in the 'System - Administrator' dropdown menu.'

I hope all this information helps in finding out what the problem is & what needs to be done.

Thanks, all.

From,
Jude

---

### Post by jdeal on 2009-04-14
I accidentally deleted my panel on my Inspiron 1525 running 8.04.01 and rebuilt it OK except the Network Monitor applet does not have the same functionality that I had before.  The one I had before (original install) produced a list of wireless (and wired) networks available with a left-click.  A right-click produced a short menu to enable wireless and a few other options I can't remember now.

The applet I have now (both use the same terminal icon) only gives a list of active devices not what networks are on the device on a left click.  A right-click gives you a properties selection but clicking that only gets you to the same device selection as a left-click.

Any idea how to get my original network applet back?  As far as I can tell, I have no choice what wireless network I am on and in-fact, I don't know which one I am on.

Thanks!

---

### Post by R2LL2R on 2009-04-16
jdeal, I've just solved this problem myself...  

After running 'profile' on startup my help button changed from a question-mark-within-blue-circle to a life-bouy? also the applet changed (which prompted me to remove it in an attempt to re-add the original, despite functionallity being the same.... OT

anyway, remove the applet you have put there, it's the network -monitor-

goto Preferences -> Network Configuration -> -RIGHT-click and select "Add this launcher to _p_anel"

it will pop up next to the help button (circle or bouy), then drag it to it's original location on the right-hand end of the panel...

Solved. this is the original network applet from 8.10 base install (for me anyways)

---

### Post by jdeal on 2009-04-18
> **R2LL2R said:**
> jdeal, I've just solved this problem myself...  

After running 'profile' on startup my help button changed from a question-mark-within-blue-circle to a life-bouy? also the applet changed (which prompted me to remove it in an attempt to re-add the original, despite functionallity being the same.... OT

anyway, remove the applet you have put there, it's the network -monitor-

goto Preferences -> Network Configuration -> -RIGHT-click and select "Add this launcher to _p_anel"

it will pop up next to the help button (circle or bouy), then drag it to it's original location on the right-hand end of the panel...

Solved. this is the original network applet from 8.10 base install (for me anyways)

Thanks but it seems Network Configuration does not exist in the Preferences or Administration menus in 8.04.

---

### Post by judeisadawson on 2009-04-19
Hi All,

It's encouraging to see this thread is still active. Thanks for the input. 

Here's what I've been doing with the problem I reported:

After doing some on-line research on this matter, I stumbled upon this site: [https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer](https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer))

Based on it's instructions, I realized that I needed 'Network Admin' installed.
So, I followed the instructions & I discovered that the 'Network Admin' application was not installed (see Illustration 1 of attachment). 

That's why I couldn't  find the 'Network' application on my machine. 
So, I downloaded it from the Ubuntu archives at [http://packages.ubuntu.com/intrepid/gnome/](http://packages.ubuntu.com/intrepid/gnome/)
and installed it in my PC.  The application installed properly to my knowledge (See Illustrations 5 & 6 of attachment).

After that, I proceeded to configure the Network Settings as per the instructions in 'Item 5.2 Connecting with a modem' of the 'Ubuntu Help Centre' documentation. I confirmed my serial modem was detected using the 'wvdialconf' command (see Illustration 2 of attachment). 

After configuring the settings , the modem auto-dialed out. I noticed on my modem that the 'In Use' LED was on and the 'Data' LED blinked a few times. I launched the 'Firefox' browser & set it to work 'on-line'. I keyed URLs of several websites but each time the error message said 'Address not Found' (see Illustration 7 of attachment) . I checked the modem & observed the 'In Use' LED was still on but the 'Data' LED was not flashing. I disconnected & repeated this several times. Each attempt had the same results.

I assumed that my earlier upgrade from Hardy to Intrepid via the alternate install CD method was missing several files and applications. As a last resort, I reformatted my PC & installed a fresh install of Interpid on my PC using the actual Intrepid install disc mailed by Canonical (thanks, guys :)). 

After I had restored all my personal files, I noticed the default Intrepid install was also missing the 'Network Settings' application and I was back at square one. So, I repeated the same above-mentioned steps and observed the same results. 

Also, I noticed several issues with the 'Network Settings', 'Modem Monitor' and 'Network Configuration' applications. My elaboration is as follows:

'Network Settings'
- Refer to Illustration 3 of attachment . Why are the ' Location' and 'green-tick' tabs greyed out? As a result, I cannot save my defined settings .
- Refer to Illustration 4 of attachment .The modem settings are correct. Each time I tick the connections box of the 'Point to point connection' selection, the modem dials out. However, why am I unable to establish a connection? 

'Modem Monitor' 
- Refer to Illustration 3 of attachment . Why are the 'Activate' and 'Deactivate' options greyed out? What does this mean?

'Network Configuration' 
- Refer to Illustration 4 of attachment . Why are most of the selections greyed out and what does this mean?
- Refer to Illustration 8 of attachment . What does 'never' refer to, what does it mean & how to change  it?

My objectives are to be able to connect to the Internet using  my serial-modem and my HSPDA 3G USB Modem. However, I need to solve these basic connection issues first before I can move on.  

I did not have much trouble getting my serial modem to connect & surf while I was on Hardy ( I did not try the 3G USB Modem on Hardy). Having moved to Intrepid is proving to be a challenge for me in the area of connecting to the Internet. Apart from this, I am very pleased with the improvements made in Intepid.

Any suggestions and comments on how I can fix these issues are greatly appreciated.

Thanks, all.

From,
Jude

---

### Post by stingray69 on 2009-04-28
I installed 9.04 last week and while customizing my panel I managed to lose the NetworkManager icon. It didn't show up as an option in "Add to Panel"  and Network Configuration isn't listed under System>Preferences. But I just saw [this post in another thread](http://ubuntuforums.org/showpost.php?p=7056092&postcount=3).

> **lovinglinux said:**
> Have you tried right-clicking the panel, then selecting "Add to Panel", then selecting "Network monitor" or "Notification Area", then the "Add" button?

Sure enough, I had removed the "Notification Area" from my panel and as soon as I added it back, I could see the NetworkManager icon.

---

### Post by jdeal on 2009-04-30
Yes.  It was the Notification applet, not the Network applet that was needed.  Brain-deadness on my part.

---

### Post by admelfo on 2009-10-17
That was it, sure as Schen-ectady -- thanks! 

Gawd. How simple! How could I not have found that.

Good call.

---

