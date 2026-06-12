---
title: "WG 111 Help"
date: 2006-04-30
forum: Networking &amp; Wireless
---

### Post by bugme on 2006-04-30
Hello,
I can't find my Netgear CD with the drivers so if anyone knows a way I could get those drivers please tell me.

Note: My Netgear WG 111 is v1 not v2

IF ANYONE HAD NETWG111.inf PLEASE SEND IT TO ME! I BEG OF YOU!
Also, once I get netwg111.inf all I have to do is 
ndiswrapper -i <directory of netwg111.inf>
right?
Thanks

---

### Post by Keith_Beef on 2006-04-30
[QUOTE=bugme]Hello,
I can't find my Netgear CD with the drivers so if anyone knows a way I could get those drivers please tell me.

Note: My Netgear WG 111 is v1 not v2

IF ANYONE HAD NETWG111.inf PLEASE SEND IT TO ME! I BEG OF YOU!
Also, once I get netwg111.inf all I have to do is 
ndiswrapper -i <directory of netwg111.inf>
right?
Thanks[/QUOTE]
Would this page be of any help?

[http://kbserver.netgear.com/release_notes/D102534.asp](http://kbserver.netgear.com/release_notes/D102534.asp)


There is a zip file, that should contain drivers for both v1 and v2 of the WG111 card.

There are also links to other troubleshooting pages.

Hope this helps.

Beef.

---

### Post by bugme on 2006-05-01
Hello,
Nice, thank you so much!
But once I acquire the driver(s) all I do in the terminal is:
sudo -s
<enter password>
ndiswrapper -i ~/driver.inf

Right?
This is considering that the driver is saved to the desktop.
Thanks! I appreciate all the help!

---

### Post by Keith_Beef on 2006-05-01
[QUOTE=bugme]Hello,
Nice, thank you so much!
But once I acquire the driver(s) all I do in the terminal is:
sudo -s
<enter password>
ndiswrapper -i ~/driver.inf

Right?
This is considering that the driver is saved to the desktop.
Thanks! I appreciate all the help![/QUOTE]

I started [a thread]("http://www.ubuntuforums.org/showthread.php?t=165964") asking questions, and ended up answering them myself.

Reading through that light straighten things out for you.


Beef.

---

### Post by bugme on 2006-05-02
Okay, nice.
Kind of funny how you fixed everything yourself.
Now I know WEP will work. By the way, if I already have a WEP key could I just enter it in in the network-admin program?
Thanks

---

### Post by Keith_Beef on 2006-05-02
[QUOTE=bugme]Okay, nice.
Kind of funny how you fixed everything yourself.
Now I know WEP will work. By the way, if I already have a WEP key could I just enter it in in the network-admin program?
Thanks[/QUOTE]

That's how I did it.

I generated a WEP key like this:
dd if=/dev/random bs=1 count=5 2>/dev/null | xxd -ps
(learned from [this]("https://www.wireless.org.au/~jhecker/wepgen/index.php") page)

This gave me a ten digit hexadecimal key,being the maximum that the NetGear router would accept.

So I entered this key in the router's configuration dialog, and in the WEP key field in network-admin.

And *bingo!*; it works.

Beef.

---

### Post by bugme on 2006-05-02
Okay,
I have acquired the driver file for my WG111v1 but when I install it in ndiswrapper it sais that it has already been installed, but when I do 
ndiswrapper -l
it sais that netwg111.inf is an invalid driver.
I downloaded the driver it said would work in the ndiswrapper list, I put the driver in ~/drivers/netwg111.inf
Please help me!
BTW, in case this helps, I have tried to install a faulty netwg111.inf before and the same errors occured.
Thanks

---

### Post by bugme on 2006-05-02
Also to add to what I said in my /etc/ndiswrapper there are 3 folders
netwg111
netwg111.cat
wg111nd5.sys

I could not delete those because It said I did not have permission to edit its parent folder. I'm guessing the folder should say netwg111.inf but it doesn't.
Those other folders were just other drivers that I attempted to install.
Thanks.

---

### Post by eternalsword on 2006-07-16
to delete those folders, you need to use the sudo command from the terminal.

cd /etc/ndiswrapper
sudo rm -r *

be sure that you run that first command otherwise you could end up deleting an entire tree of filesystem data.

---

