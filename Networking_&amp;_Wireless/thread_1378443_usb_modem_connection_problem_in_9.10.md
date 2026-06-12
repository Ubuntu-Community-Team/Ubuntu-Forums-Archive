---
title: "usb modem connection problem in 9.10"
date: 2010-01-11
forum: Networking &amp; Wireless
---

### Post by abose@linux on 2010-01-11
hi,
    i've recently bought a ZTE MG880+ modem of reliance and since then i'm trying to establish a net connection in 9.10 but failed. As i was searching for a solution i came to know about wvdial and usb modeswitch;i dwnlded both the programs in XP and installed only wvdial because i couldn't install the usb modeswitch program. But still i was able to modeswitch with the following procedure,-


[LIST=1]
[*][SIZE=2]note down the [/SIZE][SIZE=2][COLOR=Red]idvendor & idproduct with lsusb[/COLOR][/SIZE]
[*][SIZE=2][COLOR=Red]sudo chmod 777 /lib/udev/rules.d/61-mobile-action.rules[/COLOR][/SIZE]
[*][SIZE=2][COLOR=Blue]sudo gedit /lib/udev/rules.d/61-mobile-action.rules[/COLOR][/SIZE]
[*][SIZE=2][COLOR=DarkGreen]changed the default idvendor and idproduct with my own e.g 0x19d2:0xfff5[/COLOR][/SIZE]
[*][SIZE=2][COLOR=Magenta]saved the file in downloads folder with name 90-mobile-action.rules[/COLOR][/SIZE]
[*][SIZE=2][COLOR=Black]moved the file to /etc/udev/rules.d folder[/COLOR][/SIZE]
[*][SIZE=2][COLOR=Purple]reboot[/COLOR][/SIZE]
[/LIST]
After rebooting when i again plugged in the usb modem the [COLOR=Red]lsusb[/COLOR] command showed that [COLOR=Red]idvendor:idproduct=0x19d2:0xfffe[/COLOR].So i think that mode switching is done but still i'm unable to connect to internet.If anybody could pls help me on this.

---

### Post by pdc on 2010-01-11
if you have "flipped" the modem, then the next step should be setting up wvdial;

it worked for me with a ZTE modem

[http://www.geekzone.co.nz/forums.asp?forumid=46&topicid=54271](http://www.geekzone.co.nz/forums.asp?forumid=46&topicid=54271)

doing as described there:

I think some run 

> sudo wvdialconf      ....... I think ... 

...... as an initial thing first time around ......

and that does some rummaging around and offers you answers;

......... but ..........

I just copied a wvdial.conf file that George Vitas had quoted; altered the ip section to reflect the provider I was using;

details in the above

and I just dial up now by 
1) opening a terminal
2) using sudo or su depending which distro I am using
3) select the up arrow in the terminal to find wvdial 
4) hit ENTER
5) connected in about 2 secs

---

