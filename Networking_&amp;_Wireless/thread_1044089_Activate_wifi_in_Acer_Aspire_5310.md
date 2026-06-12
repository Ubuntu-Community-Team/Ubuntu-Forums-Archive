---
title: "Activate wifi in Acer Aspire 5310"
date: 2009-01-19
forum: Networking &amp; Wireless
---

### Post by ravindasenarath on 2009-01-19
i have a Acer aspire 5310 laptop and ubuntu 8.10 working in it. this laptop contain a Atheros AS5310_802.11b LAN card and working fine in windows. i am a full time linux user so i found very hard time with this problem. can any one help me to solve this.

---

### Post by afotey on 2009-01-19
Hi try this. Download this software [http://sourceforge.net/projects/madwifi/](http://sourceforge.net/projects/madwifi/)
 navigate into the folder. and execute the following commands

sudo ./configure

sudo make

sudo make install


now you reboot and voila your wireless should be working.. tell me how it goes

---

### Post by ravindasenarath on 2009-01-20
./configure didnt work for this . i try **make** . i thing it installs. but nothing happen when restrat. if it install fine wireless network should come to Network Manager Applet no?

---

### Post by afotey on 2009-01-21
ok i just checked and saw that ./configure doesn't work .. only make and make install works. so repeat the process i.e 
1. navigate into the madwifi folder,
2. sudo make
3. sudo make install
4. reboot 
and yes after sucesfull installation the wifi network will be shown on the netwok manager applet when u click on it

Also make sure that the wireless button on your laptop is on and working. U can check by going to windows and ensuring that it's on

---

### Post by afotey on 2009-01-21
ok i just checked and saw that ./configure doesn't work .. only make and make install works. so repeat the process i.e 
1. navigate into the madwifi folder,
2. sudo make
3. sudo make install
4. reboot 
and yes after sucesfull installation the wifi network will be shown on the netwok manager applet when u click on it

Also make sure that the wireless button on your laptop is on and working. U can check by going to windows and ensuring that it's on

---

### Post by ravindasenarath on 2009-01-21
sudo make install give me a error

[B]srs@srs-laptop:~/Desktop/madwifi-0.9.4$ sudo make install
sh scripts/find-madwifi-modules.sh 2.6.27-9-generic 
for i in ath/ ath_hal/ ath_rate/ net80211/; do \
		make -C $i install || exit 1; \
	done
make[1]: Entering directory `/home/srs/Desktop/madwifi-0.9.4/ath'
test -d //lib/modules/2.6.27-9-generic/net || mkdir -p //lib/modules/2.6.27-9-generic/net
install ath_pci.ko //lib/modules/2.6.27-9-generic/net
install: cannot stat `ath_pci.ko': No such file or directory
make[1]: *** [install] Error 1
make[1]: Leaving directory `/home/srs/Desktop/madwifi-0.9.4/ath'
make: *** [install-modules] Error 1[/B]

---

### Post by afotey on 2009-01-22
i think i have u the wrong link to the driver. check out this driver instead. [http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6-r3917-20090116.tar.gz](http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6-r3917-20090116.tar.gz)

and run the same commands on them. After reboot your system.. It should definately work

---

### Post by afotey on 2009-01-26
Did you try it out?? did it work?

---

### Post by ming136 on 2009-01-27
Hi, I have a similar problem.

I'm running ubuntu 8.04 on an acer travel c110.

I tried running both those madwifi files, but get a similar error.

I'm new to ubuntu.

Also i think the problem I have, is with my wifi button. Its basically a keyboard button that will turn off after a restart, but i have not gotten that to work through linux yet.

Any suggestions?

---

### Post by ravindasenarath on 2009-01-29
:D 
finally i solve this wireless problem. my friend who have the problem tall me how he found the answer.
thank you Mr.Afotey for trying to help me. its the madwifi software where i succeeded but contain some extra steps.

@ming136

if you have the same wifi adapter as i have(Atheros AR5007EG) try following link.
[http://ubuntuforums.org/showthread.php?t=902860&page=2]("http://ubuntuforums.org/showthread.php?t=902860&page=2")

---

