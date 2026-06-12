---
title: "Blank screen when xbmc is started."
date: 2010-05-02
forum: Multimedia Software
---

### Post by solitaire on 2010-05-02
Hi I've also posted this on [XBMC forums](http://forum.xbmc.org/showthread.php?t=73088)
But also posting here to see if anyone else has an idea...

I've done a clean install of Ubuntu 10.04
I'm running a Zotac Nvidia IONITX-F 330 motherboard with 4Gb ram
Nvidia drivers 195.36.24

I've got XBMC from the SVN and compiled it. (revision 29717)

here's the xbmc log file: [http://ubuntu.pastebin.com/MD2b23Rh](http://ubuntu.pastebin.com/MD2b23Rh)

If I start xbmc from a terminal window, all I see is a black screen with  the cursor.

To stop it i have to run  	Code:
 	killall xbmc.bin 
Heres the output from the terminal window:
 	Code:
 	bill@ion:~$ xbmc
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  53 (X_CreatePixmap)
  Value in failed request:  0x0
  Serial number of failed request:  146
  Current serial number in output stream:  153
/usr/local/bin/xbmc: line 88: 22174 Terminated              /usr/local/share/xbmc/xbmc.bin "$@" 
Anyone got any ideas?
*note* The same happens if i use the team-xbmc-svn ppa

If you need more info please ask...

---

### Post by Gtank on 2010-07-28
******* After over a week of searching and reading I finally figured out the blank screen with cursor issue. ********
It appears that COMPIZ is not compatible with XBMC.
The site below states to go 'to System -> Preferences -> Appearance -> Visual Effects. Make sure "None" is selected.'
[http://wiki.xbmc.org/?title=XBMC_for...ible_with_XBMC](http://wiki.xbmc.org/?title=XBMC_for...ible_with_XBMC)
 
Hope this helps.

---

