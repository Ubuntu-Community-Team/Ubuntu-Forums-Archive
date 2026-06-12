---
title: "lirc -- using two different remotes"
date: 2009-12-03
forum: Mythbuntu
---

### Post by boon2 on 2009-12-03
I've assumed for a long time that it should be possible to have two different remotes be accepted by lirc (while using only one IR receiver) and figured at some point I'd go ahead and give it a try.  Well I'm at that point now but more than a little confused by the particulars of implementing it and could really use some input.

New Karmic Mythbuntu install with a StreamZap remote and receiver already installed and working.

Would like to also use a remote that came w/ my Hauppauge pvr-150 (the silver one, 45 buttons). 

I've had the Hauppauge up and working before on a Hardy install in which I used the IR receiver that came with the pvr-150 card.  On subsequent upgrades, however, it became near impossible to get the remote/receiver working again, so I bailed on it and purchased the StreamZap which has been pretty much trouble free as far as being recognized by just about any OS I've used it with.

The StreamZap remote is kind of a clunker however, and I'd like to try to get the little Hauppauge remote pressed back into service.  I always was surpirsed how much I liked using it -- it has a nice feel.  Really didn't expect that with a remote that was merely included with the board.

At any rate, my theory is that I should be able to insert a line or three in hardware.conf, an "include" in lircd.conf which refers to the mappings for the Hauppauge, and things should spring to life.

What has me confused the most is what to add to hardware.conf -- I'm not really sure what refers to receiver vs. what refers to just the remote or how I would splice the two files together:
```

#Current StreamZap Remote Control			#Old Hauppauge remote from prev. Hardy install
REMOTE="Streamzap PC Remote"				REMOTE="Hauppauge TV card"
REMOTE_MODULES="lirc_dev lirc_streamzap"		REMOTE_MODULES="lirc_pvr150 lirc_dev lirc_i2c"
REMOTE_DRIVER=""					REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"				REMOTE_DEVICE="/dev/lirc0"
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF="streamzap/lircd.conf.streamzap"	REMOTE_LIRCD_CONF="hauppauge/lircd.conf.hauppauge"
REMOTE_LIRCD_ARGS=""					REMOTE_LIRCD_ARGS=""


#Proposed (and probably very naive) spliced version
REMOTE="Hauppauge TV card"
REMOTE="Streamzap PC Remote"
REMOTE_MODULES="lirc_dev lirc_streamzap lirc_pvr150 lirc_i2c"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_DEVICE="/dev/lirc1"
REMOTE_LIRCD_CONF="streamzap/lircd.conf.streamzap"
REMOTE_LIRCD_CONF="hauppauge/lircd.conf.hauppauge"
REMOTE_LIRCD_ARGS=""

```

????
The more I look at the above, the more skeptical I get.  And the more I realize how out of my depth I am.  If anyone could weigh in and put me on the right path or even tell me that what I want to do is not possible, I'd be very appreciative.

Thanks,
Rob

---

### Post by OffAxis on 2009-12-03
You can run two remotes on 1 receiver ONLY if the receiver can pick up on the frequency that the remote is outputting. Most remotes function in the 35 MHz range (+-5MHz). The remote's frequency should be listed in their respective lircd.conf files.


If I recall correctly (I haven't messed with LIRC in a long time) you don't have to do anything to hardware.conf

The IR receiver that you're using (and currently have defined in hardware.conf) is what both remotes are funneled through.
All you need to do is append your hauppauge's lircd.conf remote section to your currently installed one; that is, everything between the 

```
begin remote
....
end remote
```

tags.
Then restart lircd
```
sudo service lirc restart
```
and throw a 
```
irsend LIST "" ""
```

command at it (you should see both remote names show up)

irw should pick up both remotes at this point.

If your Hauppauge keys are defined differently than your streamzap's, then you'll need to match the key definitions in the lircd.conf to the lircrc file.
Either by adding a definition block in lircrc or by changing the hauppauge's key definition.
For example, if streamzap has a definition for volume as
**Vol+** and hauppauge defines it as **Vol_+** then you'll need to add a block to the lircrc OR modify the hauppauge lircd.conf key definitions to match the streamzap's (and not modify the lircrc at all)

---

### Post by azmyth on 2009-12-03
When I first started with mythtv, the lirc.conf file use to be one big file with all your remotes and transmitters in on file. I would do what OffAxis says by combining both lirc.xxx.conf files into one. Lirc will see the hex code match and pull the key press from the correct area of lirc.conf

If it complains about two remotes, then I'd try with the inlcude statement.

include "/etc/lirc/settopbox/lircd.conf.xxx"
include "/etc/lirc/settopbox/lircd.conf.yyy"

---

### Post by boon2 on 2009-12-12
Yowsa!  Got it all working finally!  Though still a little in the dark as to why I didn't have to add anything to hardware.conf to get the other remote recognized.  Oh well, as long as it's working.  Now on to getting all the mappings and jump-keys programmed. 

Many thanks to you both!

Rob

---

