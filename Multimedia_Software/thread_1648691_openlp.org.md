---
title: "openlp.org"
date: 2010-12-19
forum: Multimedia Software
---

### Post by johndavid1985 on 2010-12-19
I am using openLP.org it installed great and it works well, however i have a ccli account and it is not connecting to the ccli it continually says i need to enable cookies and javascript and i cant figure it out, please help as this is a great piece of software because i use my laptop at church

---

### Post by lykeion on 2010-12-19
Best would be to check the troubleshooting section at their [FAQ page]("http://wiki.openlp.org/OpenLP_2_Introduction_and_FAQ").

---

### Post by johndavid1985 on 2010-12-19
for some reason it wont open their help section!

---

### Post by who_da_fly on 2010-12-20
Hi johndavid1985, I'm one of the OpenLP developers. Which version of OpenLP are you using? Are you using OpenLP on Windows or Linux?

---

### Post by johndavid1985 on 2010-12-20
i am using the version for linux ubuntu,version 1.2.7

---

### Post by who_da_fly on 2010-12-20
Version 1.2.7 is for Windows only. I presume then you're running it via WINE? I don't know if the CCLI import will work in WINE because it uses the Internet Explorer engine - I haven't tried it myself.

---

### Post by johndavid1985 on 2010-12-20
also when i import a new song or even just type a new song in it continually puts a new line for each line in the verses etc?? this is something i also cannot figure out

---

### Post by who_da_fly on 2010-12-20
> **johndavid1985 said:**
> also when i import a new song or even just type a new song in it continually puts a new line for each line in the verses etc?? this is something i also cannot figure out

I don't understand what you mean.

---

### Post by johndavid1985 on 2010-12-20
i copy and paste a song into the new song feature in openlp as paragraphs etc and when i go to the "go live" button it puts every line from each verse on a separte slide

---

### Post by who_da_fly on 2010-12-20
Try pasting into gedit and then copying again from gedit (presuming you are in fact running OpenLP in WINE on Ubuntu, since you haven't actually confirmed that for me yet)?

---

### Post by johndavid1985 on 2010-12-20
sorry yes i am running it through wine because i am new to ubuntu and i could not figure out how to install int throguh ubuntu, what is gedit? and how could that help, i just copy the song to the clipboard in ccli1 not sure about things as i am very new to ubuntu

---

### Post by johndavid1985 on 2010-12-20
ok copying the word into gedit worked now the verse is to one slide instead of several sides with one line on each page. now if i can get ccli working it will be fantastic

---

### Post by who_da_fly on 2010-12-20
> **johndavid1985 said:**
> now if i can get ccli working it will be fantastic

OpenLP 1.2.7 is not supported in any way running in WINE. It is meant for Windows only. It's great if it works via WINE for most things, but "fixing" CCLI for WINE will not be happening. Version 1.2.7 is in maintenance mode.

If you want to run OpenLP natively on Ubuntu, you should look at using version 2.0 of OpenLP. The current release is 1.9.3 and it works pretty well. It doesn't have CCLI SongSelect yet, but that is in the works and will be completely cross platform.

---

### Post by wstout on 2010-12-20
johndavid1985, Your best bet is going to be to try the version intended for Ubuntu. WINE is at best a workaround and most of the time not the best at that. Since OpenLP is available albeit alpha release, it still works pretty well. Go [HERE]("https://launchpad.net/~openlp-core/+archive/release")for info on installing it in Ubuntu, click the "Read About Installing" to see how to add the package archive to your system. You will be much happier I beleive.

---

### Post by johndavid1985 on 2010-12-20
sorry not sure how to do the stuff in termial, could you possible help when it comes to terminal and other stuff i am a newbie

---

### Post by who_da_fly on 2010-12-20
> **wstout said:**
> Go [HERE]("https://launchpad.net/%7Eopenlp-core/+archive/release") for info on installing it in Ubuntu, **click the "Read About Installing"** to see how to add the package archive to your system. You will be much happier I believe.

What wstout said.

---

### Post by johndavid1985 on 2010-12-20
i did but i still dont understand,

---

### Post by wstout on 2010-12-21
johndavid1985, I will give you a walk through on this to get you going. Something you may want to look in on is how Ubuntu handles software through using repositories. This way you always have software you can trust, and receive the updates automatically. OpenLP is not in the repositories (repos) yet because it is still alpha and the developers have not gone through the process yet to get it there. So the following commands add OpenLP and its repo (personal package archive)to your system and will keep you updated when new releases are put out.

First go to applications and open up the terminal, from the terminal enter (you may want to copy and paste): ```
sudo add-apt-repository ppa:openlp-core/release
``` Then enter```
sudo apt-get update
``` this will have your system to update the packages it can receive, then enter```
sudo apt-get install openlp
``` That will install OpenLP and all the packages it needs to make it run, now that it is installed you can uninstall from the Software Center just like anything else and when you pull in updates now OpenLP will be updated when a new release is out. 

Hope that helps if you need any more help let me know

---

### Post by johndavid1985 on 2011-01-03
thanks as i said earlier i am totally new to ubuntu, i love it but just getting use to it after being pc for so long

---

