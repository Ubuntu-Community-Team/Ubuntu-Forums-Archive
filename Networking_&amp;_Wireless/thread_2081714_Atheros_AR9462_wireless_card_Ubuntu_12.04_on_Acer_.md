---
title: "Atheros AR9462 wireless card Ubuntu 12.04 on Acer Aspire V5-5"
date: 2012-11-07
forum: Networking &amp; Wireless
---

### Post by luisflores1961 on 2012-11-07
> **FoAlBo said:**
> No one able or willing to help.  Ended up re-installing 10.04.  It is supported until April 2013.  10.04 installed flawlessly found the wireless and worked immediately.  Pretty sad that 12.04 is broken and no will fix it.  Others have suggested purchasing a USB wireless device that is supported by 12.04.  Will probably do that next April.  I spent hours and hours reloading, modifying settings etc and finally gave up.  Sorry I couldn't be of help.  If I remember next April I'll add to this thread what USB wireless device ended up working.

I agree with the above statement, sadly looks like the "Precise pain golin" developers team has dropped the ball on their own end zone, I see it that bad. This is disappointing for all of us who have believed in the ubuntu project. There are a lot of request about this and none have given a real solution. Please get serious and make 12.04 the great operating system ubuntu deserves to be.
Sorry if this sound hard but all the frustration generated must get out. 
Attached you will find the requested information.

---

### Post by luisflores1961 on 2012-11-10
I found the solution here: [https://bugs.launchpad.net/linuxmint/+bug/1040943](https://bugs.launchpad.net/linuxmint/+bug/1040943) Thanks to Alexandu Stefanescu and Julien-Chales Lévesque, Stefanescu quotes this place:  [http://www.unixmen.com/resolve-slow-connexion-when-using-wifi-in-ubuntu-1104-natty-narwhal/](http://www.unixmen.com/resolve-slow-connexion-when-using-wifi-in-ubuntu-1104-natty-narwhal/)

Solution is what follows:
Open terminal and enter the following command:

sudo -s gksu gedit /etc/modprobe.d/ath9k.conf

at the end of the file add this:

options ath9k nohwcrypt=1

Save an restart your OS.

Now 12.04 is working wonderfuly.

---

