---
title: "Mythtv 0.21 frontend in 9.10 Karmic"
date: 2009-11-02
forum: Multimedia Software
---

### Post by ericwait on 2009-11-02
I just upgraded some of my computers to Karmic (9.10) and would like to run Mythtv-frontend on each but my backend is a 8.04 server running mythtv 0.21 backend.  I would like to keep it that way until I have time to upgrade the server.

Is there an easy way other then compiling mythtv 0.21 to get mythtv-frontend to work?

Thanks in advance.

Love Karmic, feels great (might be partly do to the clean install). My suspend works on my laptop! Love it!

E

---

### Post by technoboi on 2009-11-16
> **ericwait said:**
> I just upgraded some of my computers to Karmic (9.10) 
Is there an easy way other then compiling mythtv 0.21 to get mythtv-frontend to work?
E

I'm want to do this too!!

 I tried running Karmic with 0.22 and it was too broken. I installed Jaunty on my MediaCentre PC so I could use 0.21. However, I have Karmic on my desktop PC and Karmic remix on my EeePC. I too want to install 0.21 on my Desktop and EeePC running Karmic. I resorted to running Jaunty in VirtualBox, it worked but I wasn't happy with it.

So, has anyone got an easy solution?

---

### Post by Tragos on 2009-11-24
> **technoboi said:**
> So, has anyone got an easy solution?

Install Jaunty packages on Karmic. 

Download the following packages:
[http://packages.ubuntu.com/jaunty/libraw1394-8](http://packages.ubuntu.com/jaunty/libraw1394-8)
[http://packages.ubuntu.com/jaunty/libmyth-0.21-0](http://packages.ubuntu.com/jaunty/libmyth-0.21-0)
[http://packages.ubuntu.com/jaunty/mythtv-common](http://packages.ubuntu.com/jaunty/mythtv-common)
[http://packages.ubuntu.com/jaunty/mythtv-frontend](http://packages.ubuntu.com/jaunty/mythtv-frontend)

Then launch Terminal, cd to the directory where you downloaded the packages and enter the following commands:

```
sudo apt-get remove libmyth-0.22-0 mythtv-common mythtv-frontend
sudo dpkg -i *deb

```

Finally, you should pin the Jaunty version of MythTV so it won't be overwritten by the Karmic version during the next system update.

```
sudo gedit /etc/apt/preferences
```

And add the following in the file:

```
Package: mythtv-common
Pin: version 0.21.0+fixes19961-0ubuntu8
Pin-Priority: 1001

Package: mythtv-frontend
Pin: version 0.21.0+fixes19961-0ubuntu8
Pin-Priority: 1001
```

---

### Post by technoboi on 2009-11-25
> **Tragos said:**
> Install Jaunty packages on Karmic. 

Download the following packages:
[http://packages.ubuntu.com/jaunty/libraw1394-8](http://packages.ubuntu.com/jaunty/libraw1394-8)
[http://packages.ubuntu.com/jaunty/libmyth-0.21-0](http://packages.ubuntu.com/jaunty/libmyth-0.21-0)
[http://packages.ubuntu.com/jaunty/mythtv-common](http://packages.ubuntu.com/jaunty/mythtv-common)
[http://packages.ubuntu.com/jaunty/mythtv-frontend](http://packages.ubuntu.com/jaunty/mythtv-frontend)

Then launch Terminal, cd to the directory where you downloaded the packages and enter the following commands:

```
sudo apt-get remove libmyth-0.22-0 mythtv-common mythtv-frontend
sudo dpkg -i *deb

```

Finally, you should pin the Jaunty version of MythTV so it won't be overwritten by the Karmic version during the next system update.

```
sudo gedit /etc/apt/preferences
```

And add the following in the file:

```
Package: mythtv-common
Pin: version 0.21.0+fixes19961-0ubuntu8
Pin-Priority: 1001

Package: mythtv-frontend
Pin: version 0.21.0+fixes19961-0ubuntu8
Pin-Priority: 1001
```

Wow! Thanks! I'll give this a try.

---

### Post by technoboi on 2009-11-27
I did the install. It was reported that there were errors after the install. I checked dpkg.log but there were no errors in there. On a reboot there were no messages re mythtv... not that I expected any. I don't know which log to check.

After installation the link for 'MythTV Frontend' appeared in the Menu but the frontend wouldn't launch. I tried from the command line. The error reported was "6: Can't open /usr/share/mythtv/dialog_functions.sh"
I checked under /usr/share/mythtv/ but there was no file 'dialog_functions.sh'.

Any suggestions as to what I should try next?

Thank you in advance.

---

### Post by dardack on 2009-11-27
You might want to try apt-get purge instead of remove (i find remove tends to leave remnants behind).  So purge all the .22 and all the .21's and then try reinstalling .21.

---

### Post by Tragos on 2009-11-28
> **technoboi said:**
> Any suggestions as to what I should try next?

The errors you got during the installation were most likely caused by some missing packages. Try running the following from command line ```
sudo apt-get -f install
```

This should repair the package dependencies.

---

### Post by dardack on 2009-11-30
> **Tragos said:**
> The errors you got during the installation were most likely caused by some missing packages. Try running the following from command line ```
sudo apt-get -f install
```

This should repair the package dependencies.

Just be careful with that, it kept wanting to install the new mythtv for 9.10 with -f install.  I had to manually see what was missing, apt-get purge <package i had just tried to install from that list>, then apt-get install <missing dependency>, took me maybe 20 minutes total, but it works great.

---

### Post by bernied on 2009-12-05
I think there's a better way of doing this. Use the old packages from the jaunty repositories, and pin the version to 0.21.

Details on [this thread](http://www.mythtvtalk.com/forum/general/12097-cant-use-0-21-0-22-fe.html) on the mythtv forums.

But now I don't have sound in mythtv. Anyone else got this issue with v0.21 in karmic?

---

### Post by technoboi on 2009-12-11
Firstly, thank you to Tragos for his help. I also learned how to stop updates from this - very useful! I had already tried 'purge' earlier, as dardack suggested, but doing it again AND mucking around a little in the Synaptic Manager, got the Frontend working. Thanks!!

> **bernied said:**
> I think there's a better way of doing this. Use the old packages from the jaunty repositories, and pin the version to 0.21.

Details on [this thread](http://www.mythtvtalk.com/forum/general/12097-cant-use-0-21-0-22-fe.html) on the mythtv forums.

But now I don't have sound in mythtv. Anyone else got this issue with v0.21 in karmic?
I have heard of people generally having sound problems in Karmic but as yours is specific to MythTV then there may be a simple answer.
Have you checked out the settings (Frontend) under Utilities/Setup>Setup>General> Audio is 3rd screen. Mucking with the 'Audio Output Device' and 'Mixer Controls' might help.
My settings are:-
'Audio Output Device' /dev/dsp
'Passthrough output device' Default (there's only one option - Alsa - on mine)
'Mixer Controls' Master
Then use:-
F10 Down volume
F11 Up volume
F9  Mute/Unmute

Hope this helps!:)

---

### Post by bernied on 2009-12-19
> **technoboi said:**
> Firstly, thank you to Tragos for his help. I also learned how to stop updates from this - very useful! I had already tried 'purge' earlier, as dardack suggested, but doing it again AND mucking around a little in the Synaptic Manager, got the Frontend working. Thanks!!


I have heard of people generally having sound problems in Karmic but as yours is specific to MythTV then there may be a simple answer.
Have you checked out the settings (Frontend) under Utilities/Setup>Setup>General> Audio is 3rd screen. Mucking with the 'Audio Output Device' and 'Mixer Controls' might help.
My settings are:-
'Audio Output Device' /dev/dsp
'Passthrough output device' Default (there's only one option - Alsa - on mine)
'Mixer Controls' Master
Then use:-
F10 Down volume
F11 Up volume
F9  Mute/Unmute

Hope this helps!:)

Thanks for taking the trouble to reply. There was a simple answer, I just got rid of pulse audio, which is the new default for ubuntu, but doesn't play well with mythtv.

---

### Post by undy on 2010-01-15
> **Tragos said:**
> Install Jaunty packages on Karmic. 

Download the following packages:
[http://packages.ubuntu.com/jaunty/libraw1394-8](http://packages.ubuntu.com/jaunty/libraw1394-8)
[http://packages.ubuntu.com/jaunty/libmyth-0.21-0](http://packages.ubuntu.com/jaunty/libmyth-0.21-0)
[http://packages.ubuntu.com/jaunty/mythtv-common](http://packages.ubuntu.com/jaunty/mythtv-common)
[http://packages.ubuntu.com/jaunty/mythtv-frontend](http://packages.ubuntu.com/jaunty/mythtv-frontend)

Then launch Terminal, cd to the directory where you downloaded the packages and enter the following commands:


etc
:
:


For anyone coming on this thread down the track:

I tried the bernied method which resulted in an unmet dependency mess. Then I re-installed 0.22 for 9.10, and followed Tragos' guide and all was good.

Thanks all.

(Oh yeah, the front-end is on an eeepc running remix, like technobi's)

---

### Post by technoboi on 2010-01-15
Now that the final version of MythTV 0.22 is included in Karmic, rather than the broken RC, the situation has changed much for the better. I am posting this because I am sure that many, like me, search the forums for solutions.
With Karmic, and the final release of MythTV 0.22, nearly all seems to be working well, I can now even get BBC HD!

However, some problems (as always) are still are evident....

What doesn't work for me is the transport editor in MythTV backend - all I get is a blank page. I wanted to include a transport for ITV HD. 
I tried adding the transport manually to the database, from the command line, into 'channelscan_dtv_multiplex' - it added OK but maybe that is the wrong table because there was no joy there either :-(
Does anyone know a suitable setup procedure to get ITV HD?

The other problem, which has long existed with MythTV, is that when restarting the computer the tuners change order and that mucks up everything - I have a 500T Terrestrial dual tuner card and a Hauppauge S2 satellite card. The only way I have found round this is to close down, switch off the PSU, and boot from cold. I tried blacklisting/whitelisting of modules but It wasn't successful - perhaps I got the module names wrong or otherwise, I don't know.

One other problem I am getting, previously not seen, is that the TV screen goes to sleep every few minutes, even in playback, and I have to keep waking it up via the keyboard. I've checked Ubuntu 'Power Saving' but I can't see anything there that would cause it. The TV works OK on standard TV transmissions.... so I am currently at a loss on this one.
:)

---

### Post by bernied on 2010-01-24
This is just to say that I've also now upgraded to 0.22. I have none of the troubles that technoboi is suffering from, but I've only got the one receiver card (also a DVB 500T).

I've got one frontend running Kubuntu 9.10, and had few troubles upgrading using aptitude.

For my backend, which runs Debian, I was paranoid and did a new install of the whole OS and Myth, then migrated the database. But this was because I never had any spare time, my earlier install was a bloated mess, and I didn't want to have any unwanted downtime on the backend. Loads of issues setting that up, but generally they were my fault.

---

### Post by technoboi on 2010-01-24
I found out why the screen was going to sleep every 5 minutes. It wasn't the power saving, it was the screen saver - something I never use so it was just a blank screen. 
That problem is solved and the system seems to be stable now except for the tuner order problem, on boot-up, as mentioned before.

---

### Post by windom on 2010-01-25
I am using LinHES as my main front/back mythtv in the TV room. I am using karmic on my laptop. I have no choice but drop back to mythtv0.21 on my laptop to use it as a remote frontend. I followed the instructions laid out by Tragos and the adjusted the sound options as mentioned earlier in this thread. This led to much joy.

Thanks to all who made this possible.

windom

---

### Post by rowlandm on 2010-04-02
> **bernied said:**
> I think there's a better way of doing this. Use the old packages from the jaunty repositories, and pin the version to 0.21.

Details on [this thread](http://www.mythtvtalk.com/forum/general/12097-cant-use-0-21-0-22-fe.html) on the mythtv forums.

But now I don't have sound in mythtv. Anyone else got this issue with v0.21 in karmic?

This is what I did in 10.04 Beta Lucid Lynx

Setup MythTV 0.21 front end for Lucid Lynx

1) sudo gedit /etc/apt/sources.list

#added
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) jaunty universe
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) jaunty universe
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) jaunty multiverse



2) sudo gedit /etc/apt/preferences 

# created brand new file
# pinning mythtv to stay at v0.21 for compatibility with backend
Package: mythtv
Pin: version 0.21*
Pin-priority: 1001

Package: mythtv-common
Pin: version 0.21*
Pin-priority: 1001

Package: mythtv-frontend
Pin: version 0.21*
Pin-priority: 1001

3) sudo apt-get update

4) Download and install this package manually (ie dpkg -i *.deb or open in debi program and install ) as it must be located somewhere else in Jaunty

[http://packages.ubuntu.com/jaunty/libraw1394-8](http://packages.ubuntu.com/jaunty/libraw1394-8)

5) sudo apt-get install mythtv-frontend

6) Setup mythtv frontend - worked perfectly, sound and everything!

Thanks very much to the two posts below that helped me set this up!

[http://www.mythtvtalk.com/forum/general/12097-cant-use-0-21-0-22-fe.html](http://www.mythtvtalk.com/forum/general/12097-cant-use-0-21-0-22-fe.html)

[http://ubuntuforums.org/showpost.php?p=8380319&postcount=3](http://ubuntuforums.org/showpost.php?p=8380319&postcount=3)

---

### Post by technoboi on 2010-04-02
You'll see, in an earlier posting, in this thread, I have commented on the Audio settings. I find that this needs to be set differently depending on the hardware as well as OS version.
The very latest version of MythTV does work well in Karmic, with a few caveats as listed below. I have done several installations. A friend uses an Acer Revo as a frontend only. That needed setting to HDMI to hear the sound on the TV via HDMI.
I don't run the sound on the TV, it goes via the HiFi.
Just try mucking with the sound settings*, in MythTV, and see if this helps.
*Menu:   Utilities/Setup>Setup>General>    Audio is 3rd screen

The only remaining problems I get with MythTV are:-
1. The random boot order of cards.
2. Regular crashing - not fully investigated but,as this is often through the night, I put it down to not getting the right response when getting the EPG.
3. Delete screen bug (goes to Watch Recordings). I just press 'D', on the appropriate recording, whilst in 'Watch Recordings' anyway.(I prefer to use a wireless keyboard rather than a standard remote control)
4. I run a frontend on my Desktop computer. Without booting the frontend, just as the computer boot normally, there is constant accessing of the Disk. There have been postings on this with a supposed cure, but I find that it doesn't work. I simply close down the unwanted backend on the Desktop and then everything goes quiet. I find that stopping the backend booting, in the first place, doesn't work. It just leaves you with a problem of constant disk access and no way to switch it off. So, it looks like it is a program that is triggered separately to the backend - very strange. So, if running a remote frontend make sure that you are not getting this. It doesn't occur on all installations for reasons unknown.

---

### Post by dblade on 2010-05-09
> **rowlandm said:**
> This is what I did in 10.04 Beta Lucid Lynx

Setup MythTV 0.21 front end for Lucid Lynx
[..]


Thanks for posting this solution.  Upgrading all boxes at once in order to use mythtv just won't happen.

---

### Post by undy on 2011-07-19
My mythtv environment has run so well for the last two years, its become a family-requirement, so upgrading the backend is tough.

I upgraded my eeepc to 11.04 and the front-end spat the dummy at the old backend. I needed to revert to the 0.23.0 frontend.

I finally found this thread again - followed the instructions from **Tragos** again, this time grab the following from Lucid:

libmyth-0.23-0_0.23.0+fixes24158-0ubuntu2_i386.deb
libraw1394-11_2.0.4-1ubuntu2_i386.deb
mythtv-common_0.23.0+fixes24158-0ubuntu2_i386.deb
mythtv-frontend_0.23.0+fixes24158-0ubuntu2_i386.deb

and pin with:
```
Package: mythtv-common
Pin: version 0.23.0+fixes24158-0ubuntu2
Pin-Priority: 1001

Package: mythtv-frontend
Pin: version 0.23.0+fixes24158-0ubuntu2
Pin-Priority: 1001
```

---

