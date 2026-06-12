---
title: "HOWTO: Old amarok"
date: 2009-06-25
forum: Multimedia Software
---

### Post by henky on 2009-06-25
Hey guys, I got this from someone else so the credit goes to: poloking!
Anyway this is about howto get tamarok 1.4 instead of the pesky new one supplied with kde4


Open up your sources file
Code:

sudo nano /etc/apt/sources.list

Go right to the bottom and input the sources which have the old amarok, on seperate lines:
Code:

deb [http://ppa.launchpad.net/bogdanb/ppa/ubuntu](http://ppa.launchpad.net/bogdanb/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/bogdanb/ppa/ubuntu](http://ppa.launchpad.net/bogdanb/ppa/ubuntu) jaunty main

ctrl-o to save ctrl-x to exit

then to add the key:
Code:

sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com \
0x1d7e9dd033e89ba781e32a24b9f1c432ae74ae63

Update your sources:
Code:

sudo apt-get update

Remove amarok2 and install amarok1.4:
Code:

sudo apt-get remove amarok
sudo apt-get install amarok14

---

### Post by philcamlin on 2009-06-25
cool

why would we need the old one though? :popcorn:

---

### Post by henky on 2009-06-27
> **philcamlin said:**
> cool

why would we need the old one though? :popcorn:

cuz there are sum ppl like me who think the new amarok sucks BIG time:)

---

### Post by NickLondon28 on 2009-06-29
Excellent... I also think the new Amarok is rubbish

---

### Post by echaz on 2009-07-12
Dude, 

Thanks so much (I registered an account for this message).  

Amarok2 blows.  What were the developers thinking?  They had the best ipod support of anybody other than apple, and they messed it all up with that awful thing. 

I would be able to deal with it if it could just load a playlist onto my ipod with it.  Oh, and it crashes all the time.

---

### Post by I_Like_Pie on 2009-07-15
> **NickLondon28 said:**
> Excellent... I also think the new Amarok is rubbish


I agree...Amarok 1.X is the reason I went to Linux...if 2.0 were there I would have NEVER made the jump.

Amarok went from the best player to the worst in one simple version change...very sad feelings for the people who put the hard work into it.

---

### Post by Barafu Albino Cheetah on 2009-10-30
I wonder, why didn't anybody fork it. KDE 4.3.2 is out, and new Amarok is still an absolute trash.

---

### Post by zenkaon on 2009-10-30
Does wikipedia and album art lookup work in the 1.4 version???

I am thinking of upgrading my living room media pc from 9.04 to 9.10, it's currently using amarok 1.4 and wikipedia and album art doesn't work.

My laptop has ubuntu 9.10 and amarok 2, it's getting a bit better, and wikipedia and album art lookup works in the new amarok.

So, big question is do these things now work in amarok 1.4???

---

### Post by SuperSonic4 on 2009-10-30
Fair enough, Amarok 2 is fast getting better. Does Karmic ship with version 2.2?

---

### Post by zenkaon on 2009-10-30
On karmic the amarok version is 2.2.0 (using KDE 4.3.2)

It's a LOT better than previous 2.x versions and actually a contender for amarok 1.4s crown......I'll see how I get on with it.

Having album art lookup and wikipedia working again is a big plus

---

