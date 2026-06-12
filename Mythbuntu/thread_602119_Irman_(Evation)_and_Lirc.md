---
title: "Irman (Evation) and Lirc"
date: 2007-11-03
forum: Mythbuntu
---

### Post by cenwesi on 2007-11-03
Hi guys, i don't know if this is the right place to ask this question.
I have about 4 Irman (evation) serial devices here. I have been trying for the past 2weeks to get this to work with ubuntu + MythBuntu but no luck. I have tried just about every website that shows how to install lirc but still no luck getting ubuntu to read this device. Can someone out there that has theirs working please post a howto. 

PS. I am trying to try use mythtv for HTPC.

---

### Post by cenwesi on 2007-11-05
So many people viewing this but not one response. I really don't want to go by MCE remote just to get this working.

---

### Post by OffAxis on 2007-11-05
I'm not familiar with the irman and their website isn't coming up...
Is this a receiver, transmitter (blaster) , or both?

is lirc installed?

**lircd -v**
will tell you what version you're using.

Do you have your 
**/etc/lirc/lircd.conf** set up?

---

### Post by cenwesi on 2007-11-05
The Irman by Evation is a serial reciever. It looks like this
[http://www.intolect.com/irmandetail.htm](http://www.intolect.com/irmandetail.htm)

It is similar (or the same) to one of those home brew serial recievers.

I have tried different lirc... But  "lircd 0.8.2" is the one currently installed.

here is the remote code i downloaded to use with my Hauppauge remote. 

#
# this config file was automatically generated
# using lirc-0.6.4(any) on Mon Jan 28 19:49:15 2002
#
# contributed by
#
# brand:                       hauppauge
# model no. of remote control:
# supported devices:
#

begin remote

  name  hauppauge
  bits           16
  eps            30
  aeps          100

  one             0     0
  zero            0     0
  pre_data_bits   16
  pre_data       0xFFFF
  post_data_bits  32
  post_data      0x0
  gap          209960
  min_repeat      6
  toggle_bit      0


      begin codes
          TV                       0x000000000000FE00
          RADIO                    0x000000000000FE60
          MUTE                     0x000000000000FE40
          FULLSCREEN               0x000000000000FA20
          SOURCE                   0x000000000000FBA0
          RESERVED                 0x000000000000FC20
          MINIMIZE                 0x000000000000FB20
          CH+                      0x000000000000FBE0
          CH-                      0x000000000000FBC0
          VOL+                     0x000000000000FDE0
          VOL-                     0x000000000000FDC0
          1                        0x000000000000FFC0
          2                        0x000000000000FFA0
          3                        0x000000000000FF80
          4                        0x000000000000FF60
          5                        0x000000000000FF40
          6                        0x000000000000FF20
          7                        0x000000000000FF00
          8                        0x000000000000FEE0
          9                        0x000000000000FEC0
          0                        0x000000000000FFE0
      end codes

end remote
#
# this config file was automatically generated
# using lirc-0.7.0pre2(irman) on Wed Feb 18 23:58:38 2004
#
# contributed by Ben Buxton <bb|bb.cactii.net>
#
# brand:                       hauppauge
# model no. of remote control:
# devices being controlled by this remote: Nova-T DVB PCI Card
#

begin remote

  name  hauppauge
  bits           16
  eps            30
  aeps          100

  one             0     0
  zero            0     0
  pre_data_bits   16
  pre_data       0xFFFF
  post_data_bits  32
  post_data      0x0
  gap          213188
  min_repeat      8
  toggle_bit      0


      begin codes
          POWER                    0x0000000000002A80
          GO                       0x0000000000002AE0
          1                        0x0000000000002940
          2                        0x0000000000002970
          3                        0x0000000000002960
          4                        0x0000000000002910
          5                        0x0000000000002900
          6                        0x0000000000002930
          7                        0x0000000000002920
          8                        0x00000000000029D0
          9                        0x00000000000029C0
          BACKEXIT                 0x00000000000028A0
          0                        0x0000000000002950
          MENU                     0x0000000000002980
          RED                      0x00000000000029E0
          GREEN                    0x0000000000002BB0
          YELLOW                   0x0000000000002AD0
          BLUE                     0x0000000000002BC0
          UP                       0x0000000000002B50
          DOWN                     0x0000000000002B40
          LEFT                     0x0000000000002840
          RIGHT                    0x0000000000002850
          OK                       0x0000000000002B00
          MUTE                     0x00000000000029A0
          _BLANK                   0x0000000000002990
          FULL                     0x0000000000002A90
          REW                      0x0000000000002A70
          PLAY                     0x0000000000002A00
          FWD                      0x0000000000002A10
          REC                      0x0000000000002A20
          STOP                     0x0000000000002A30
          PAUSE                    0x0000000000002A50
          REPLAY                   0x0000000000002B10
          SKIP                     0x00000000000028B0
      end codes

end remote

---

### Post by OffAxis on 2007-11-05
I think there's a mistake with your lircd.conf;
you should only have one 'remote' section with the name 'hauppauge'.

I see that you got your conf file from the lirc website, but I also read somewhere (i think in the lirc docs) that two devices cannot have the same name.
Edit: Yup. it is in the docs. right [here ]("http://winlirc.sourceforge.net/technicaldetails.html")
> You may not assign the same name to two different remotes in the same configuration file.
delete or comment out (#) one instance of 'hauppauge' and reload lirc.

from (and including)

#begin remote
#...
#end remote


```
sudo /etc/init.d/lirc restart
```

then try an
```
irsend LIST "" ""
```

your entry in lircd.conf should come up; you should get
**irsend: hauppauge**

what do you get?

and which hauppauge remote are you using?

---

### Post by OffAxis on 2007-11-05
you also mentioned that you've tried every website on installing lirc that you've come across, but if you haven't tried the ubuntu specific site for gutsy yet, it's a worthwhile endeavor.

[https://help.ubuntu.com/community/Install_Lirc_Gutsy]("https://help.ubuntu.com/community/Install_Lirc_Gutsy")

---

### Post by cenwesi on 2007-11-05
Let me begin by thanking you.. i forgot to mention that in the previous post.  Thank you :)

Ok down to business.  I didn't even notice that the file had both sections there. Anyway deleted one out and restarted lirc which started fine. I  issued your command and i get my prompt back and no hauppauge.

Here is the remote i am using. [http://www.hauppauge.com/images/new_remote.jpg](http://www.hauppauge.com/images/new_remote.jpg)

One other thing i should mention is that i currently run SageTV using this remote and the IRman....Works fine but i really want to test out MythTV and switch completely to linux but this is the only thing standing in my way right now :)

BTW, i have been to that site and others.... I will uninstall the lirc and redo it again using the Gusty version. Maybe i miss something.

---

### Post by OffAxis on 2007-11-05
I just checked the lirc homepage.
Turns out, irman support is busted in 8.2 (your current version and the current version in repos). So the only option for using it is the cvs build.
Instructions are here:
[http://www.lirc.org/cvs.html]("http://www.lirc.org/cvs.html")

---

### Post by cenwesi on 2007-11-05
Ok,  I will uninstall again and see if i can figure out how to install it using the CVS. Any pointers here?

---

### Post by OffAxis on 2007-11-05
the install looks straightforward according to the directions on the lirc page. I've never done a build of it so I've got no advice aside from don't forget to have the required build tools installed;
[B]automake1.10
libtool
autoconf[/B]

Good luck.

---

