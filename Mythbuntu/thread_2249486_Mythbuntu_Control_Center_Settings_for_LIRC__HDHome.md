---
title: "Mythbuntu Control Center Settings for LIRC / HDHomeRun"
date: 2014-10-22
forum: Mythbuntu
---

### Post by bryan32 on 2014-10-22
I have Mythbuntu combined frontend/backend set up with a Silicon Dust HDHomeRun receiver and generic satellite IR remote control.

I manually created the hardware.conf file and key mappings file.In the Mythbuntu Control Center under 'Infrared' I have the "USB and Serial Support via LIRC ..."  radio button checked (and no receiver or transmitter selected) to be sure the LIRC package stays installed, but every time the LIRC package gets an update, it overwrites my custom hardware.conf file with a generic one (and sometimes additional files), which requires me to manually copy over the correct files and restart the Lirc daemon.

What are the proper MCC settings for this set-up so my custom files don't get over-written?, or 
How do I prevent my custom files from getting over-written with each LIRCD package update?

This is either a LIRC package configuration bug (it should keep/restore custom settings files) or there should be a MCC setting to alert to a custom setup (maybe I've missed the setting).

---

### Post by neutron68 on 2014-10-27
Good questions!

The exact same thing happened to me, just one week after I got LIRC working with my serial IR receiver/transmitter and Mythbuntu 12.04LTS (with myth 0.25).
I changed repositories to the mythtv 0.27 and updated...WHAM.  My IR remote suddenly didn't work any more.
Luckily, I had made copies of the files with .backup at the end of the filenames.

Another question:  When the user's IR remote isn't in the IR remote list, could the Mythbuntu Control Centre (MCC) scripts be tweaked so they would ask the user for the file location of an existing lircd.conf file?

---

### Post by bryan32 on 2014-10-28
> **neutron68 said:**
> Good questions!The exact same thing happened to me, just one week after I got LIRC working with my serial IR receiver/transmitter and Mythbuntu 12.04LTS (with myth 0.25).I changed repositories to the mythtv 0.27 and updated...WHAM.  My IR remote suddenly didn't work any more.Luckily, I had made copies of the files with .backup at the end of the filenames.Another question:  When the user's IR remote isn't in the IR remote list, could the Mythbuntu Control Centre (MCC) scripts be tweaked so they would ask the user for the file location of an existing lircd.conf file?That is a great suggestion. I am hoping to hear how others using an IR remote with HDHomeRun handle this situation. I keep thinking there must be a setting I am missing instead of correcting the over-written files each time.

---

### Post by neutron68 on 2014-11-18
Hi Mythbuntu developers, 

Where can we discuss improvements such as these LIRC setup improvement ideas?
Here?  Somewhere else?

Eric

---

### Post by dannyboy79 on 2014-11-19
you may be able to catch them live on the irc channel on freenode, it's #mythbuntu i believe otherwise just be patient and hopefully a dev will get back you here. there may even be a way to email them if you checked out the mythbuntu website but that's up to you

but if you guys are looking for a way to prevent a mythbuntu update from changing your irc setup than I would suggest digging into how lirc actually works, finding out which lirc config files mythbuntu is using and then just copy the applicable files and store them in your home directory so if lirc stops working on you, you can simply use the copy you saved to overwrite the new lirc files that were put there by the update. good luck

---

### Post by bryan32 on 2014-11-19
I believe that is what I and neutron68 are presently doing. We have to revert to backup lirc configuration files whenever there is an update. My original question was possibly I am choosing the wrong settings in the mythbuntu control center and that is why my custom files are getting overwritten (or there should be a setting called custom, which doesn't clobber original custom configuration files each time there is an update (unless their is a major configuration file format change, in which case the proper behavior would be to copy the old custom file to a .bak file (or similar) before copying the new default configuration file, so it doesn't just clobber custom files.

---

### Post by dannyboy79 on 2014-11-19
as i said you need to review the documentation of lirc and lircd to see where local user config files are read from. basically there's 2 config files for almost all linux packages, the system ones located in /etc/ or /usr/lib/ and then user conf files located in your home folder. what the software does is first reads the system conf files and then will read the users conf files so apparently mythbuntu must only be editing the system conf files for lirc and lircd so when an update occurs your changes get overwritten. i find this hard to believe that the dev's didn't think of this already and i'm surprised about the behavior your seeing but if it's happening it's happening.  so I just suggest finding out what conf directories lircd and lirc processes read and then just put your conf files there. you could do a find for lircd.conf and lircrc

you can check it out here: [https://www.mythtv.org/wiki/LIRC#Set_up](https://www.mythtv.org/wiki/LIRC#Set_up)

---

### Post by neutron68 on 2014-11-25
> **dannyboy79 said:**
> as i said you need to review the documentation of lirc and lircd to see where local user config files are read from. 
Hi.  We're not asking how to set up LIRC.  We already have all the config files where they need to be in the system and LIRC is working.  
> **dannyboy79 said:**
> i find this hard to believe that the dev's didn't think of this already and i'm surprised about the behavior your seeing but if it's happening it's happening.Exactly.  More than one of us are seeing the same behavior.  The behavior is confirmed.
> **dannyboy79 said:**
> so I just suggest finding out what conf directories lircd and lirc processes read and then just put your conf files there. you could do a find for lircd.conf and lircrc

you can check it out here: [https://www.mythtv.org/wiki/LIRC#Set_up](https://www.mythtv.org/wiki/LIRC#Set_up)Already did that.  We had to do this in order to get LIRC working - no need to do it again.  
Please note, that the Mythbuntu information on that mythtv wiki page on LIRC is from 2011 at best.  Mythbuntu setup has changed a bit since 2011.
After some research on the LIRC process in Mythbuntu, I wrote up a how-to for getting LIRC to work with Mythbuntu 12.04 LTS (currently supported).
The later part of [the thread]("http://ubuntuforums.org/showthread.php?t=2246603") lists my setup procedure, step-by-step.

Right now, our goal is to see if we can get the Mythbuntu setup utility revised so it checks before it blindly overwrites existing LIRC config files.

Eric

---

