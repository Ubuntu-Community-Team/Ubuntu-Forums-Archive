---
title: "Printer wireless networking issues"
date: 2010-06-11
forum: Networking &amp; Wireless
---

### Post by BurningSludge on 2010-06-11
[FONT=Arial Black]I am having problems connecting to an HP Officejet  6500 E709n. I am trying to get it connected  via an ad hoc connection via the printer's wireless radio. I have been trying to get it connected for nearly a month. I have HPLIP and I tried getting it connected via the wizard 8 times. MY Toshiba Satellite L455D can see the printer but I can't send a job to the printer even if I seem to be connected to the printer. I can connect and print using the USB cable.[/FONT]

---

### Post by BurningSludge on 2010-06-12
[FONT=Comic Sans MS][SIZE=3]Help:confused:[/SIZE][/FONT]

---

### Post by jnorthr on 2010-06-12
are you using ubuntu ? if so, what flavor and version please ?

---

### Post by jnorthr on 2010-06-12
just looked the spec for your HP Officejet 6500  and it says it does NOT have wireless. Are you SURE it has a wireless feature ?

---

### Post by BurningSludge on 2010-06-12
[FONT=Comic Sans MS][SIZE=3]I am using Ubuntu 10.04 and I am quite sure that the model I'm using does indeed have wireless capabilities. I can still connect and print successfully on my Windows 7 partition.[/SIZE][/FONT]

---

### Post by jnorthr on 2010-06-12
found this on launchpad answers: [https://answers.launchpad.net/hplip/+question/110822](https://answers.launchpad.net/hplip/+question/110822)

they are suggesting an uninstall and re-install of the CUPS printer sub-system as a poss. cure

---

### Post by jnorthr on 2010-06-12
keep this link for later, if you need it:
[http://www.dodownload.net/index.php?s=officejet+6500](http://www.dodownload.net/index.php?s=officejet+6500)

not sure if you do or donot need this for 10.04, but maybe for w/7

---

### Post by jnorthr on 2010-06-12
looking here: [http://hplipopensource.com/hplip-web...ces/index.html](http://hplipopensource.com/hplip-web...ces/index.html)
for choices, there are four possibilities for the 6500 all-in-one - did you take the choice for hplip E709N ?

---

### Post by BurningSludge on 2010-06-13
[FONT=Comic Sans MS][SIZE=3]Okay, reinstalling CUPS was not a solution. All it did was force me to install Printing from the software center but the good news is that everything is working as good as it has before I removed cups this afternoon. The whole problem seems like a connection issue but my Wi-Fi works with networks other than the printer. If it helps printer's network has both the normal wave symbol and one that looks like a wave symbol in a computer monitor.[/SIZE][/FONT]

---

### Post by 987a654 on 2010-06-24
sorry for bumping your thread.

I have the same problem with a brother hl2170w printer, I am using 10.04, mine works perfectly on vista but not on ubuntu. It just does not connect to the printer, keeps trying. 

"The whole problem seems like a connection issue but my Wi-Fi works with networks other than the printer. If it helps printer's network has both the normal wave symbol and one that looks like a wave symbol in a computer monitor."

This is same with me.
Any help?

yudi

p.s

Just after posting this I found these links
[http://www.ubuntugeek.com/creating-an-adhoc-host-with-ubuntu.html](http://www.ubuntugeek.com/creating-an-adhoc-host-with-ubuntu.html)
[https://help.ubuntu.com/community/WifiDocs/Adhoc](https://help.ubuntu.com/community/WifiDocs/Adhoc)

Now at least I can connect to the network.

yudi

---

