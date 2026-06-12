---
title: "Channel Changing script for a Cisco d9865"
date: 2011-12-28
forum: Mythbuntu
---

### Post by Meph1st0 on 2011-12-28
I'm attempting to get my myth box to work with my shiny new AFN decoder.  It's a Cisco d9865.  Previous AFN decoders were made by Scientific Atlantic and now that company has been bought out by Cisco.  If I'm not mistaken (which I frequently am) I need to create a new channel changing script for this new STB.  I've never done this before and don't even know where to begin.

I've ordered a IR blaster and have yet to receive it.  However, I've got a device I can use to record the IR codes from the remote.  I figure I might be able to get a head start on it.  I have not been able to find any remote codes anywhere on the interwebs.  I've only seen threads where others are attempting to get the same information.

I'm using a PC-HDTV 5500 tuner card (specified as MJPEG capture Card in mythtv-setup) with the setup that I'll only be using as a capture card to capture from the coax output from the decoder.  I believe I've set it up correctly so far in mythtv-setup except for the "external channel change command".  In the mythtv wiki it shows /usr/bin/ch_chan.sh in that field but I don't see that file in my install.  Thought maybe Mythbuntu might have moved the channel changing scripts to a different directory but I don't know where.

I've also seen the Mythchanger utility but that appears to only be used with firewire capable STBs.  Unfortunately this STB is not equipped with firewire.

Any further input on this would be hugely appreciated.  Is there anyone else out there attempting to use Mythtv with the new AFN Cisco d9865?

---

### Post by jobcol on 2011-12-29
hi
did you have a previously working Channel Change script from a previous STB?

---

### Post by Meph1st0 on 2011-12-29
I don't.  I don't even know where most people get them.  I figure that might be the route to go though.  Get a script for a different STB and attempt to adjust it for this box.  I'm guessing the best one to start with might be one of the Scientific Atlantic ones since I'm guessing Cisco (after having bought out SA) just modified one of their products.

---

### Post by jobcol on 2011-12-29
ok
so first of all your're gonna need a working lircd.conf file for this new remote, once you have that, the channel change script is easy. you can just modify an existing one for your remote.
check here to find one that works for your remote
[http://lirc.sourceforge.net/remotes/](http://lirc.sourceforge.net/remotes/)

---

### Post by jobcol on 2011-12-29
the closest match to your STB I could find is for a Scientific Atlanta  d9835 satellite receiver:
[http://lirc.sourceforge.net/remotes/scientific_atlanta/RM9834](http://lirc.sourceforge.net/remotes/scientific_atlanta/RM9834)

i would try this lircd.conf file to see if it works for your STB, theres a good chance it will

---

### Post by Meph1st0 on 2011-12-29
I'm a little confused about that.  Are you telling me that I'm now going to use the remote that came with my STB to control my mythbox?  Up until now I've been using the remote that came with my htpc case (Zalman HD135).  I thought I'd continue to use the same remote as before to control myth and then the IR Blaster would control the STB to change channels.  Do I need an additional lircd.conf file for the IR blaster? Or just modify the one I have to work with both the HTPC remote and the IR Blaster?

---

### Post by jobcol on 2011-12-29
You can still use your old remote, but in order for Mythtv, or more specifically lirc, to be able to control your new STB through your IR blaster, it needs to know the infra-red codes,frequencies etc. that your new remote uses to control the new STB.
This info is contained in the lircd.conf file.So you need to add the new lircd.conf file for your new remote to your existing /etc/lirc/lircd.conf file.
Once you have a working lircd.conf file for your new remote you can then give this data to Mythtv and lirc ( by editing the .lircrc file) so your new STB can be controlled with your old remote. 
Also your new channel change script will based off the lircd.conf file for your new remote.

---

