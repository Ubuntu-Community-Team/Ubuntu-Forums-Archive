---
title: "nxclient fails using gdm chooser"
date: 2009-11-24
forum: Networking &amp; Wireless
---

### Post by lisanels47 on 2009-11-24
When using GDM as the chooser, NXclient fails to connect to shadow sessions because the sessions are owned by root.  I switched choosers to KDM, and then it worked perfectly.  This happened with GDM about a year ago as well, and they fixed it.  But it's broke again.  Below are the details of the connection errors you will get.  I'm also attaching two screenshots, one for gdm, and one for kdm....

 Display Type                Session ID               Services depth  Screensize  Status   Session Name Username
------- ------------ -------------------------------- -------- ----  -------------- ----------- --------------------- ----------------
0       X11-local    CC6C68ED81D4C5098FE26A53C37 --D--PSA N/A  N/A            Running     Local display         root                            
NX> 105 Listsession --type="shadow" 
NX> 127 Session list possible to attach:: 

 Display Type                Session ID               Services depth  Screensize  Status   Session Name Username
------- ------------ -------------------------------- -------- ----  -------------- ----------- --------------------- ----------------
0       X11-local    CC6C681CED84C5984126A53C37 --D--PSA N/A  N/A            Running     Local display         root                            
NX> 105 Attachsession --link="adsl" --backingstore="1" --encryption="1" --cache="16M" --images="64M" --shmem="1" --shpix="1" --strict="0" --composite="1" --media="0" --session="Remote-Randy-Shadow" --type="shadow" --client="linux" --keyboard="pc105\057us" --id="CC6C681CED81D4C5098412FE26A53C37" --display="0" --geometry="N\057A" 
NX> 596 ERROR: Cannot share session of user: root.
NX> 596 ERROR: User: root is not a NX user.
NX> 105 NX> 280 Exiting on signal: 15

---

### Post by lisanels47 on 2009-11-28
Well, after trying to switch back from KDM to GDM, my system is messed up.  I can struggle and get KDM working again, but GDM is another story.  I've tried uninstalling all references to GDM, and reinstalling.  Same problem.  Talk about unfriendly packages.... I know there's something in the configuration that got wacked, but I have yet to find it....

---

