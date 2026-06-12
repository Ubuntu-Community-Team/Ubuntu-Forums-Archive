---
title: "post your .lircrc file"
date: 2007-11-12
forum: Mythbuntu
---

### Post by cenwesi on 2007-11-12
Can someone please post their .lircrc file. How come MythTV just doesn't respond to some of the buttons on my MCE remote.

---

### Post by uopjohnson on 2007-11-12
Its only going to help if someone with your remote posts their .lircrc.  A better path is just to modify your own for the buttons that don't work.  
Open up a terminal and type:
```
irw
```
Then start pressing buttons on your remote.  You should see them reflected on your terminal.  Try out some that work already to see what it looks like and then start pressing the ones that don't work.  You will see an ir code (which you can ignore) and the name of the button (which you should write down or remember).
type cntrl-c to kill irw. 
Then start editing your .llircrc file by coping stanzas taht work and replacing the Button = line with the name of your button from above and the config = line with a key from yrou keyboard that you want myth to recognize.

---

### Post by cenwesi on 2007-11-13
I see all the buttons when i run "irw" but on MythTV for example on the MythTV screen, when i press the "LiveTV" screen, nothing happens. Its like the only buttons that work are up/down/left/right/ok/stop/0-9/enter. You will think that telling mythtv what type of remote you have and it copies the .lircrc file that i will have all the correct mapping. Trying to get info on how to reprogram their lircrc file is a pain. Anyway maybe someone can help me figure this out because i a somewhat lost.

---

### Post by superm1 on 2007-11-13
After you've sorted out what mappings are missing, please file a bug against mythbuntu-lirc-generator with what remote you have and what you needed to add to make it work so that future versions can properly work with your remote.

---

### Post by uopjohnson on 2007-11-13
If you post which buttons are missing and what irw says I can help you edit your lircrc file.

---

### Post by jimbo1954 on 2007-12-10
I have exactly the same problem. Lirc is correctly identifying my remote, and irw sees correct strings for each button push. However, in Myth, all I get is up/down/left/right/enter/power.

I have tried lircrc files that I have created correctly, and some from others who know better than me, and they all result in the same outcome.

When I press the remote keys with a terminal window open, I get the same result, so I'm beginning to think that lircrc is not actually being read or used. The keyboard controls work properly, so Myth is responding to input correctly, the remote is inputting correctly (irw shows this), there is just a disconnect between the two.

dmesg is clean, as is syslog. This is all reproducable on a fresh install of 7.10, Gutsy..

Any help would be greatly appreciated, I'm trying to get this working on an old Philips MT1400 Freevents, which should have ample power for the job, this current build being a Proof-of-Concept before I spend serious money on a proper silent, high-power HTPC rig.

Cheers
Jim

---

### Post by uopjohnson on 2007-12-10
These two steps should help with this:
1) update yoru system to get the latest lirc generator for mythbuntu.
2) In the control center under remote control check the Generate dynamic button mappings box and hit apply.

---

### Post by cyrus_the_virus on 2007-12-26
Hi,

I think I have the same problem. I'm trying to use a Pinnacle PCTV remote control and when I run *irw* everything works fine but in mythtv only 2 buttons work (but the way these buttons are mapped to the actions are not logical)

The channel- on my remote provides the down button, and the arrow up on my remote provides the up button.

I have made my own lircrc files and I've put it in all possible folders:
~/lircrc
~/.lircrc
/etc/lircrc
/etc/.lircrc
But it doesn't change anything and I don't understand why! I can't figure out what lircrc file is actually used because the way mythtv is responding to my remote is very different from the way I programmed the lircrc file :(

Marty

---

### Post by superm1 on 2007-12-26
> **cyrus_the_virus said:**
> Hi,

I think I have the same problem. I'm trying to use a Pinnacle PCTV remote control and when I run *irw* everything works fine but in mythtv only 2 buttons work (but the way these buttons are mapped to the actions are not logical)

The channel- on my remote provides the down button, and the arrow up on my remote provides the up button.

I have made my own lircrc files and I've put it in all possible folders:
~/lircrc
~/.lircrc
/etc/lircrc
/etc/.lircrc
But it doesn't change anything and I don't understand why! I can't figure out what lircrc file is actually used because the way mythtv is responding to my remote is very different from the way I programmed the lircrc file :(

Marty
~/.mythtv/lircrc

---

### Post by arjay1 on 2007-12-28
Hi all - there is another thread running on this issue but I don't know how to insert a link to it here - sorry.  It is called "Newbie confused about how to configure PVR 350 remote" in the Mythbuntu forum.

I also have the same problem with a Hauppauge pvr150 remote (new silver type) and in that post I described it thus to superm1:

> 
superm1 - the buttons that don't work are those like TV, TV guide pictures, video, radio, etc round the top of the remote and the four coloured ones along the bottom. However, at least you have helped to get the main ones working - the pvr stuff in the middle.


superm1 replied:
> 
Ah yeah, those buttons don't have support right now for **any** remotes atm. Can you file a bug against mythbuntu-lirc-generator to remind us to get to those?

I tried to work out how to file the bug but never found how to do it.  If someone else would like to do that instead of me, it would be good.

Cheers.

---

### Post by superm1 on 2007-12-29
> **arjay1 said:**
> 
I tried to work out how to file the bug but never found how to do it.  If someone else would like to do that instead of me, it would be good.

Cheers.

[https://bugs.launchpad.net/mythbuntu/+filebug](https://bugs.launchpad.net/mythbuntu/+filebug)

---

