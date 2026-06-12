---
title: "flashplayer for youtube"
date: 2010-11-22
forum: Multimedia Software
---

### Post by objet petit a on 2010-11-22
Hello everybody, 

I have just completed my Ubuntu install and I am happy (for now). But life wouldn't be life without a little trouble in paradise. In this case I cannot play the Youtube video&#347;. I tried simply following the links, but that gave me an error-message saying it was a virtual file. Apparently I cannot open it. So, I checked the package manager, but nothing for flash players.

Is there anyone who knows what I should try?

---

### Post by cpmman on 2010-11-22
Try _***[Flash-aid]("https://addons.mozilla.org/en-US/firefox/addon/161939/")***_ from lovinglinux

---

### Post by TBABill on 2010-11-22
In a terminal ```
sudo apt-get install ubuntu-restricted-extras
``` or go to Ubuntu Software Center or Synaptic and install it.
 
Just a friendly reminder - since Linux will not run Windows applications natively, be careful of attempting to install codecs or other software directly from links. The repositories have a vast (thousands) amount of software for most needs and assistance can be gotten from users or previous posts on how to install software from outside the repos correctly.

---

### Post by lisati on 2010-11-22
I have the player from adobe installed. Seems to work OK on 10.04 64-bit.

---

### Post by bonixavier on 2010-11-22
Download the player [from Adobe]("http://get.adobe.com/br/flashplayer/"). If the Ubuntu specific version doesn't work, download the .tar.gz one and manually place the extracted file into /usr/lib/mozilla/plugins.

---

### Post by jimmers on 2010-11-22
Try this, follow in sequence.
  	 	 	 	p { margin-bottom: 0.21cm; }  sudo add-apt-repository ppa:neversfelde/minitube  sudo apt-get update  sudo apt-get install minitube

---

### Post by ngrieb on 2010-11-22
Um, is this a 64 bit install of a 32 bit install?

---

### Post by objet petit a on 2010-11-23
It&#347; a 64 bit install, why is that important?

Oh, and thanks everybody! I am thinking of going to the adobe site btw. It would be the first manual install I have tried, so it would be a learning experience.
:)

---

### Post by objet petit a on 2010-11-23
> **bonixavier said:**
> Download the player [from Adobe]("http://get.adobe.com/br/flashplayer/"). If the Ubuntu specific version doesn't work, download the .tar.gz one and manually place the extracted file into /usr/lib/mozilla/plugins.
Hi, I have extracted the tar.gz, but I am not allowed to write in the specified folder. If I am correct I should use chmod. I am looking at this page:
[http://manpages.ubuntu.com/manpages/karmic/man2/chmod.2.html](http://manpages.ubuntu.com/manpages/karmic/man2/chmod.2.html)
Should I use:
 **S_IWUSR**  (00200)  write by owner

??

would the command be chmod 00200 then?

---

### Post by bonixavier on 2010-11-23
You don't have the permissions to write in that folder because you're a regular user. You'll have to either move it through nautilus using "gksudo nautilus" or start a root shell by typing "sudo su"

Don't touch the permissions for the the folder.

Before installing, make sure you've downloaded the correct version.

---

### Post by objet petit a on 2010-11-23
Okay, I have placed the extracted file in the desired folder, but the utube movies still show the same update message. What is wrong?

---

### Post by b0b138 on 2010-11-23
download the 64bit plugin from here [http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

Go into symantec and search flash and remove any other versions of flash.

place the extracted file into ~/.mozilla/plugins folder

---

### Post by objet petit a on 2010-11-23
Okay, there are several scripts in the folder. How do I know which to remove?

---

### Post by objet petit a on 2010-11-24
> **TBABill said:**
> In a terminal ```
sudo apt-get install ubuntu-restricted-extras
``` or go to Ubuntu Software Center or Synaptic and install it.
 
Just a friendly reminder - since Linux will not run Windows applications natively, be careful of attempting to install codecs or other software directly from links. The repositories have a vast (thousands) amount of software for most needs and assistance can be gotten from users or previous posts on how to install software from outside the repos correctly.
I used your code in the terminal and it works great!

Thanks a lot!!!

---

