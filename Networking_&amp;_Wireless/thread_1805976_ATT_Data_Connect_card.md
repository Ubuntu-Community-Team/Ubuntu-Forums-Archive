---
title: "ATT Data Connect card"
date: 2011-07-16
forum: Networking &amp; Wireless
---

### Post by sks24 on 2011-07-16
I'm trying to get an ATT wireless usb card running on a Dell 3000 Tower running 10.04.2.

I would like to first ask whether or not others have gotten this fellow running, as the manufacture is not listed amongst the supported cards.

Modem manuf: Option N.V. 
Model: G10461
Hardware ID: OPTIONBUS\GTHSV41_MDM
Device Driver: GlobeTrotter G14xx -Modem interface#2
2.14 .2.0Hd  

The APN used is isp.cingular.

The second question I have has to do with tar.gz files.  I downloaded the one listed [here]("http://peck.org.uk/ozerocdoff.html") in order to stop the "ZeroCD" on the card from running, but I don't know how to "open up a console and change to the directory where the package was downloaded."

The card runs fine on the XP side of this tower.  

I do understand that there's a procedure for wireless postings, and I know how to do that.  But I'm thinking that we need to get ozerocdoff running first before we do the postings of the output upon "lspci" and so forth.  Well, and also whether the card will "work" at all.

Thank you in advance,
Scott

---

### Post by sks24 on 2011-07-17
Progress:
I think I've got ozerocdoff installed:

```
afl-cio@afl-cio-desktop:~$ cd ~/Downloads
afl-cio@afl-cio-desktop:~/Downloads$ cd ~/udev
bash: cd: /home/afl-cio/udev: No such file or directory
afl-cio@afl-cio-desktop:~/Downloads$ cd udev
afl-cio@afl-cio-desktop:~/Downloads/udev$ sudo make
[sudo] password for afl-cio: 
make: Nothing to be done for `all'.
afl-cio@afl-cio-desktop:~/Downloads/udev$ sudo make install
install -d /usr/sbin
install -d /etc/udev/rules.d
install ozerocdoff /usr/sbin
cp hso.udev /etc/udev/rules.d/51-hso-udev.rules
install -d /usr/share/hal/fdi/preprobe/20thirdparty
cp 10-wwan-hso-preprobe.fdi /usr/share/hal/fdi/preprobe/20thirdparty
install -d /usr/share/hal/fdi/information/20thirdparty
cp 10-wwan-quirk.fdi /usr/share/hal/fdi/information/20thirdparty
install -d /usr/lib/hal/scripts/
install hal-serial-hsotype /usr/lib/hal/scripts/
install -d /etc
install osetsuspend /usr/sbin
cp hso-suspend.conf /etc
afl-cio@afl-cio-desktop:~/Downloads/udev$ 

```

However, the "ZeroCD" still auto starts when I plug it in.  

It says [here]("http://peck.org.uk/ozerocdoff.html"):

[INDENT]If you have installed this utility and it does not seem to work check the following:

1. ozercdoff UDEV rules require a dialout group. If it does not exist create the group
2. Make sure root and your user name are in the dialout group.[/INDENT]

I can't find a how-to having to do with gaining rights via adding this user to the "dialout" group.  I have to step out for an hour or so.  If someone could point me in the right direction w/r/t this task, it would be great, as I only have today to get the Internet going on the Ubuntu side of this computer.

---

### Post by smcrossman on 2011-07-17
I am using a Laptop Connect card...(intermal, but same setup) which I just had to re-work because I dropped my home dsl and had to pick up tehtering on my iPhone to extend my internet access.

Regardless...I had not set up the AT&T card for broadband in Linux since I mostly used my  netbook at home or at hotspots. In fact I hadn't used linux outside of my home network/wifi area.

If it isnt' working wtih the isp.cingulair (which is being phased out) try using option for Broadband (there are 3 Mobile Broadband listings under AT&T....media net, Laptop Connect and Data Connect.  Also the number under basic should be *99***1# or *99***2# or *99***3#.  usually data connect/laptop connect is 1#, phones are 3#. I was told if you need to enter some kind of extra initialization string use the 3#. 

I actually spent a bit of time on the phone with wireless tech support yesterday and got a rep who although unfamiliar with linux was willing to share information on basic setup, and sent me many emails he had received from a previous customer trying to get up & running in linux. I didn't need the emails. I set up 2 broadband profiles one for the DataConnect and one for the LaptopConnect
and then made the one that connected automatic connection.

I will be going through the emails to see if I can figure out using the iPhone tethering via bluetooth (or wifi although he said that wasn't possible) rather than wired. but at least I have access for the moment.

For mobile use there is no security, no user id/password or network id but of course with your tower you would set up whatever security your router/gateway would require (if you are accessing the ATT mobile then its all blank)  I think if you use the correct number in the basic and APN in Advanced it should work pretty much like it does in XP.  The basic information is all the same as what the info sheets say to use in Windows.  If you need them I can probably forward copies of the relevant info the rep sent me via email.

---

### Post by sks24 on 2011-07-18
Thanks so much smcrossman

Well, can't get it going.  Here's the message upon entering "/usr/sbin/pppd call gprs" in a terminal per the instructions:

```
afl-cio@afl-cio-desktop:~$ /usr/sbin/pppd call gprs
/usr/sbin/pppd: In file /etc/ppp/peers/gprs: unrecognized option '/dev/modem'
```

The instructions you emailed me appear to be identical to the ones listed here:  [http://www.wireless.att.com/answer-center/panels/solution/printSolution.jsp?solutionId=36059&t=solutionTab&ft=&ps=solutionPanels&locale=en_US&_dyncharset=UTF-8&viewMode=NORMAL&windowType=SAME&highlightInfo=&isRecord=false](http://www.wireless.att.com/answer-center/panels/solution/printSolution.jsp?solutionId=36059&t=solutionTab&ft=&ps=solutionPanels&locale=en_US&_dyncharset=UTF-8&viewMode=NORMAL&windowType=SAME&highlightInfo=&isRecord=false)

I would really, really like it if someone could walk me through this sometime.  These people really, really, REALLY need a working Linux partition, and the one I've installed for them is useless at present because their cruddy ATT device won't play with Ubuntu.

Thanks,
Scott

---

