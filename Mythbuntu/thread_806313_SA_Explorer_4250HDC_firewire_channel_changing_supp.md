---
title: "SA Explorer 4250HDC firewire channel changing support?"
date: 2008-05-24
forum: Mythbuntu
---

### Post by stratoscape on 2008-05-24
I hope this is not like beating a dead horse but I have spent the better part of the last 10 day researching and banging around trying to get Majors SA4250_ch channel changer to work for me over firewire. There are so many post out there where lots of people have worked on it but not a single person ever posted what finally worked for them.

I am not a Linux user in fact it has been several years since I last used it. I am about as green as green gets so try not to bust a nut laughing at me :) 

I am currently running ubuntu 8.0.4 on my laptop and setting up myth on my Fedora8 box. most of the post on this issue seem to be non version specific so I like this board better so I'm posting my question here and hoping for the best

I have a PVR-500 twin tuner card connecting to (2) SA4240HDC STB's with all the necessary libs and mods loading (I think lol)

[root@localhost tmp]# yum list|grep 1394
ieee1394-kmdl-2.6.24.7-92.fc8.i686       2.6.24.3-5.fc8         installed       
libavc1394.i386                          0.5.3-1.fc6            installed       
libdc1394.i386                           2.0.1-10.fc8           installed       
libdc1394-docs.i386                      2.0.1-3.fc8            installed       
libdc1394_22.i386                        2.0.1-10.fc8           installed       
libdc1394_control12.i386                 1.2.2-8.fc8            installed       
libraw1394.i386                          1.3.0-8_11.fc8         installed       
libraw1394_8.i386                        1.3.0-8_11.fc8         installed       
ieee1394.i386                            2.6.24.3-5.fc8         atrpms          
ieee1394-kmdl-2.6.24.7-92.fc8.i586       2.6.24.3-5.fc8         atrpms          
ieee1394-kmdl-2.6.24.7-92.fc8PAE.i686    2.6.24.3-5.fc8         atrpms          
ieee1394-kmdl-2.6.24.7-92_1.cubbi_tuxoni 2.6.24.3-5.fc8         atrpms          
ieee1394-kmdl-2.6.24.7-92_1.cubbi_tuxoni 2.6.24.3-5.fc8         atrpms          
ieee1394-kmdl-2.6.24.7-92_1.cubbi_tuxoni 2.6.24.3-5.fc8         atrpms          
libavc1394-devel.i386                    0.5.3-1.fc6            fedora          
libdc1394-devel.i386                     2.0.1-10.fc8           atrpms          
libdc1394-tools.i386                     2.0.1-3.fc8            updates         
libraw1394-devel.i386                    1.3.0-8_11.fc8         atrpms          


[root@localhost tmp]# lsmod|grep 1394
raw1394                24152  0 
dv1394                 19000  0 
ohci1394               29872  1 dv1394
ieee1394               74420  3 raw1394,dv1394,ohci1394

When I run Majors firewire channel changer SA4250_ch (which I compiled on my ubuntu laptop as I could not figure out how to do it in fedora8 ) I get this:

[root@localhost tmp]# ./sa4250_ch -v 704
node 0: vendor_id = 0x000010dc model_id = 0x00000000
Device acquired on node 0
Changing channel 704
AV/C Command: cmd0=0x00487ce7 cmd1=0x0402c000 cmd2=0xff000000

A previous post from MajorIdiot suggest that changing ports on the stb may resolve this however, in my case it did not. sa4250_ch indicates it is changing the channel to 704 but noting happens. I also tested running this without the firewire plugged in just out of curiosity

[root@localhost tmp]# ./sa4250_ch -v
Couldn't get 1394 handle: No such file or directory
Is ieee1394, driver, and raw1394 loaded?  Are /dev/raw1394 permissions set correctly?

SA4250_ch naturally failed as the necessary files are not loaded because    there is no STB detected on the 1394 port.
  
Something else I wondered was how does the SA4250_CH know which STB or node to change the channel on. for now a question I can live not knowing the answer to as the channels are not changin anyway :)

Finally I ran plugreport which to the common noob looks like it indeed picks up both STB which are connected to a PCI firewire expansion card. it has 3 ports (2 external 1 internal) I think this is why it picks up nodes 0 and 2 instead of 0 and 1 since they are side by side this confused me as well but I figured node 1 on adapter 1 must be the internal 1394 port on the pci card. The other Host adapter 0 (connected to mobo by dongle) and Host adapter 2 is the 1394 port on the Soundblaster Audigy card.

[root@localhost tmp]# plugreport
Host Adapter 0
==============

Node 0 GUID 0x0010dc000041a4ab
------------------------------
libiec61883 error: error reading oMPR
libiec61883 error: error reading iMPR

Host Adapter 1
==============

Node 0 GUID 0x001ceada8fec0000
------------------------------
oMPR n_plugs=1, data_rate=2, bcast_channel=63
oPCR[0] online=1, bcast_connection=0, n_p2p_connections=0
        channel=0, data_rate=0, overhead_id=0, payload=146
iMPR n_plugs=0, data_rate=2

Node 1 GUID 0x005042a12363c64f
------------------------------
libiec61883 error: error reading oMPR
libiec61883 error: error reading iMPR

Node 2 GUID 0x001ceadaa71a0000
------------------------------
oMPR n_plugs=1, data_rate=2, bcast_channel=63
oPCR[0] online=1, bcast_connection=0, n_p2p_connections=0
        channel=0, data_rate=0, overhead_id=0, payload=146
iMPR n_plugs=0, data_rate=2

Host Adapter 2
==============

Node 0 GUID 0x00023c0020004a67
------------------------------
libiec61883 error: error reading oMPR
libiec61883 error: error reading iMPR


Anyway apologies for the length of the post and thanks in advance for your attention

Strato

---

### Post by bml137 on 2008-08-19
I was having an issue with mine, and found a solution with a slight change to Major's code.  See the other thread:

[http://ohioloco.ubuntuforums.org/showthread.php?t=712789](http://ohioloco.ubuntuforums.org/showthread.php?t=712789)

---

