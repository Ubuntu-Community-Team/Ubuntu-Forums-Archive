---
title: "[SOLVED] codecs won't install?"
date: 2008-12-11
forum: Multimedia Software
---

### Post by ToyotaGuy23 on 2008-12-11
I did some wiki searching for why my videos won't play and did this:
[B]
sudo apt-get install ubuntu-restricted-extras[/B]

Terminal said:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
ubuntu-restricted-extras is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.27-7 linux-headers-2.6.27-7-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

I then tried:
[B]
 sudo apt-get install w32codecs[/B]

Terminal said:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package w32codecs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package w32codecs has no installation candidate

Please forgive me for being new but,
What should I do, and where should I go to get codecs to play my files?

Thanks

---

### Post by binbash on 2008-12-11
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by ToyotaGuy23 on 2008-12-11
I tried the Totem player which didn't work. 

I went to a player called Kaffeine from the repos, and tried VLC also from the repos.  

What is the preferred player?

---

### Post by ToyotaGuy23 on 2008-12-11
Thanks for the reply.

Now, I've entered:
[B]
 sudo wget [http://www.medibuntu.org/sources.list.d/intrepid.list](http://www.medibuntu.org/sources.list.d/intrepid.list) --output-document=/etc/apt/sources.list.d/medibuntu.list[/B]

And Terminal Said:

--2008-12-11 11:14:13--  [http://www.medibuntu.org/sources.list.d/intrepid.list](http://www.medibuntu.org/sources.list.d/intrepid.list)
Resolving [www.medibuntu.org](www.medibuntu.org)... 87.98.242.110
Connecting to [www.medibuntu.org|87.98.242.110|:80](www.medibuntu.org|87.98.242.110|:80)... connected.
HTTP request sent, awaiting response... 200 OK
Length: 230 [text/plain]
Saving to: `/etc/apt/sources.list.d/medibuntu.list'

100%[======================================>] 230         --.-K/s   in 0s      

2008-12-11 11:14:13 (13.6 MB/s) - `/etc/apt/sources.list.d/medibuntu.list' saved [230/230]

I still have the same results.
What am I doing wrong?

---

### Post by ToyotaGuy23 on 2008-12-11
OK I learned what I did should have put Medibuntu in the repos.

I went into the repos, and it asked me to update, I said OK. 

I got an error that said:

W: GPG Error: The following signatures couldn't be verified because the public key is not correct.  

Hmmm what now?

---

### Post by binbash on 2008-12-11
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

Please read the page which i linked.Everything is there.

---

### Post by ToyotaGuy23 on 2008-12-11
Thanks, I appreciate your help.

Unfortunately, I having trouble with the page you suggested because of this step.
[B]
"Add Medibuntu to your sources.list, as well as its GPG key to your keyring. Make sure to use the correct sources.list that corresponds to your current distribution."[/B]

Please do not get frustrated, I am still new to Ubuntu, and learning as I go.  

Thanks again

---

### Post by ToyotaGuy23 on 2008-12-11
I've been chasing this stuff all day, link after link.  

As per instructions [here]("https://help.ubuntu.com/community/Repositories/Ubuntu"), I don't even HAVE the reload button to click.

I'm putting more time into setup than use.

*Sigh*

---

### Post by 2hot6ft2 on 2008-12-11
Here you go all that you asked for is here.

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

Close synaptic before using the terminal which can be found under Applications>Accessories>Terminal

Oh, by the way I use vlc it seems to work best for me

---

### Post by ToyotaGuy23 on 2008-12-11
> **2hot6ft2 said:**
> Here you go all that you asked for is here.

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

Close synaptic before using the terminal which can be found under Applications>Accessories>Terminal

Oh, by the way I use vlc it seems to work best for me

THANK YOU so much, that tutorial was EXACTLY what I was looking for!

---

### Post by 2hot6ft2 on 2008-12-11
You're welcome. Enjoy

---

