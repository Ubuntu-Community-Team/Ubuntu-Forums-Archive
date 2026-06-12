---
title: "DNS setting lost every time after reboot"
date: 2006-06-04
forum: Networking &amp; Wireless
---

### Post by e_liming on 2006-06-04
I dont have a wifi card. I use my Intel NIC. I don't have Network-Mananger installed.

Now I find my DNS setting lost everything I reboot my PC. And the biggest problem is: this still happens even I edit /etc/resolv.conf manually... 

:-?

---

### Post by virtual_void on 2006-06-04
It sound like the DNS server is not setup properly. The /etc/resolv.conf will be overwritten by the DHCP client when it gets is address lease.

The real error is in the server, but you could add
  prepend domain-name-servers <IP-FOR-YOUR-DNS-SERVER>
first in
  /etc/dhcp3/dhclient.conf
as a temporary workaround.

---

### Post by e_liming on 2006-06-04
Sorry forgot to mention, I use static IP address.

---

### Post by thieste on 2006-09-11
well, i had the same Problem... you just need to remove the package *resolvconf*.

---

### Post by madmetal on 2006-09-11
i have the same problem..
i should just remove resolvconf, make some changes or    is there a way to do this [http://www.ubuntuforums.org/showthread.php?t=255494](http://www.ubuntuforums.org/showthread.php?t=255494) 
 ?

---

### Post by emix on 2006-09-15
Simply delete /etc/resolvconf/run/enable-updates to prevent resolvconf updating your resolv.conf. It's an empty file that is used by resolvconf as a flag.

---

### Post by Free_As_In_Freedom on 2006-09-27
> **emix said:**
> Simply delete /etc/resolvconf/run/enable-updates to prevent resolvconf updating your resolv.conf. It's an empty file that is used by resolvconf as a flag.

It didn't work for me because that *!@ file (enable-updates) was back again at every boot.](*,) 
The real working solution (to me of course), without messing up or deleting files or uninstalling packages was doing this (after a little man resolvconf): 
```
sudo cp /etc/resolvconf/resolv.conf.d/original /etc/resolvconf/resolv.conf.d/tail
```
before doing this, would be better to check if your "/etc/resolvconf/resolv.conf.d/original" already contains your static nameserver IP address (nameserver xxx.xxx.xxx.xxx); in other words if you put a string with "nameserver xxx.xxx.xxx.xxx" (replace x's with your nameserver's IP) on the empty "/etc/resolvconf/resolv.conf.d/tail" your baby will remember that address at every boot (well it worked for my dapper anyway) :D
Hope it will be helpful. :)

---

### Post by handy on 2006-09-27
I have been having the same problem, (I don't have a static IP).

I have tried many solutions, since last November 2005, when I took up Breezy.  The Breezy solution is not applicable to Dapper.

I have had success's, but allways I know they are messy, not the correct way.

& strangely, what works for one system, doesn't work for another? :confused: 

This seems to me to be a bug in Ubuntu.  That many of us will be relieved to see squashed. ](*,) 

If you find it difficult to resolve this problem, (as the same solution seems not to work for everyone) links follow:-

[http://ubuntuforums.org/showthread.php?t=245618](http://ubuntuforums.org/showthread.php?t=245618)

[http://www.ubuntuforums.org/showthread.php?t=202053&highlight=dhclient.conf](http://www.ubuntuforums.org/showthread.php?t=202053&highlight=dhclient.conf)

[http://ubuntuforums.org/showthread.php?t=252967&page=2](http://ubuntuforums.org/showthread.php?t=252967&page=2)

---

### Post by handy on 2006-09-28
> **emix said:**
> Simply delete /etc/resolvconf/run/enable-updates to prevent resolvconf updating your resolv.conf. It's an empty file that is used by resolvconf as a flag.

The aforementioned directory **/etc/resolvconf/** doesn't exist on my machine...

---

### Post by bigken on 2006-09-28
I got round this problem by doing this in my router 

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=16474&stc=1&d=1159448937[/IMG]

---

### Post by wieman01 on 2006-09-28
> **handy said:**
> The aforementioned directory **/etc/resolvconf/** doesn't exist on my machine...
I guess it's more likely"
> /etc/resolv.conf

---

### Post by wieman01 on 2006-09-28
This is something I have never tried myself but I am sure you could revoke the files "write" rights...
> sudo chmod -w-w-w /etc/resolv.conf
...After entering your DNS. An idea without knowing if it works or not.

---

### Post by bigken on 2006-09-28
> **wieman01 said:**
> I guess it's more likely"

yep your right ;) /etc/resolv.conf

---

### Post by handy on 2006-09-28
If you looked the links I put up in a previous post you would see I have used the following, which worked, but It still seems to me that it shouldn't have to be done like this:

I just edited the **/etc/dhcp3/dhclient.conf**

removing - **domain-name-servers**

Then after entering the correct DNS IP addresses of my ISP, into the **/etc/resolv.conf** & making it *immutable* with the following line:

**sudo chattr +i /etc/resolv.conf**

So, the above works for me. 

I've also tried the following on it's own:

[I]You can force your own dns servers when using dhcp by putting:

**supersede domain-name-servers x.x.x.x**;

in your **/etc/dhcp3/dhclient.conf** where x.x.x.x is your preferred dns server (you can enter multiple servers seperated by a space)[/I]

This was not quite right either, due to my router's IP hijacking the settings by writing itself in first place after rebooting (not after every reboot though :confused:  )

So I've now put my routers address in last using the above method, & I'll see how that goes before I make the **resolv.conf** file immutable again.

I just checked & my router/modem's address was back in first place again...  So I will revert to the immutable method again.

All in all it's a bit messy... :-k

---

### Post by handy on 2006-09-28
> **bigken said:**
> I got round this problem by doing this in my router 

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=16474&stc=1&d=1159448937[/IMG]

My router doesn't make it as straight forward as yours.

The other problem I have is that my ISP changes their DNS addresses quite often...

---

### Post by redcharlie on 2006-09-28
My /etc/resolv.conf is a link to /var/run/resolvcof/resolf.conf

root@k7som-5c:~# chattr +i /var/run/resolvconf/resolv.conf

chattr: Inappropriate ioctl for device while reading flags on /var/run/resolvconf/resolv.conf

---

### Post by handy on 2006-09-29
I am out of my depth here...

All I can contribute is that when I change my DNS addresses via the Ubuntu ***Menu:* System / Administration / Networking** the changes are directly reflected in my **/etc/resolv.conf** & visa versa.

So, my logic can see that if I put the DNS addresses in the **/etc/resolv.conf** & make it immutable, then it should stay that way until I change it.

Which does seem to be the only one that has worked & kept on working for me so far...

---

### Post by wieman01 on 2006-09-29
Actually... The file that controls the DNS settings is:
> /etc/network/interfaces
"/etc/resolv.conf" is only temporary & updated while the computer is booting. Show me your "interfaces" file and I tell you how to fix the DNS...

---

### Post by handy on 2006-09-29
> **wieman01 said:**
> Actually... The file that controls the DNS settings is:

"/etc/resolv.conf" is only temporary & updated while the computer is booting. Show me your "interfaces" file and I tell you how to fix the DNS...

I'm all ears... (eyes actually :rolleyes:  )
------------------------
[I][B]auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp[/B][/I]

---

### Post by wieman01 on 2006-09-29
Add this line under your wireless device. E.g.:
> auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
[COLOR="Red"]dns-nameservers xxx.xxx.xxx.xxx[/COLOR]
Assuming that "eth0" is the device you are referring to & [COLOR="Red"]xxx.xxx.xxx.xxx[/COLOR] being the DNS of your choice. Just move the line if to the right place if "eth0" is not the one.

Then restart the network:
> sudo /etc/init.d/networking restart

---

### Post by handy on 2006-09-29
> **wieman01 said:**
> 

Assuming that "eth0" is the device you are referring to & [COLOR="Red"]xxx.xxx.xxx.xxx[/COLOR] being the DNS of your choice. Just move the line if to the right place if "eth0" is not the one.

Then restart the network:

sudo /etc/init.d/networking restart


Thankyou :cool: 

I'll undo my other mod's & follow your recomendation now.

Then I'll test for a few days (or less if there is a problem) & report here.

I do like the look of your solution...

---

### Post by handy on 2006-09-29
I checked my Networking settings after restarting the network as per previous post, & found that the router's IP had been put in above the other 2 (this stops me from being able to access the repo's).

Also, something I hadn't mentioned before, is that 1 of the 2 DNS addresses that I have put in, is now superseded.  I put the correct one in days ago, & very recently as per the above thread, (deleted all from resolv.conf before rebooting) after rebooting the router's IP is not there (yet) but still one of the DNS addresses is wrong?  As it has been since I put it in.  Something is changing the right one for the wrong one when I boot the machine?

These DNS addresses must be stored somewhere else that I don't know about?

Any ideas?

---

### Post by wieman01 on 2006-09-29
When using DHCP the your computer is assigned your IPS's DNS addresses. Check your router... You can find them somewhere there.

Could you try replacing xxx.xxx.xxx.xxx with this address:
> dns-nameservers 208.67.222.222
That's an open DNS... Just to see whether it stick. Then reboot and open resolv.conf.

---

### Post by handy on 2006-09-29
Thanks for your reply... :) 

The router is where I get my DNS addresses from.  I have to check it every so often because (as previously stated) my ISP changes the addresses whenever it sees fit!

I will make your requested change before I shut down tonight & see what I've got when I boot in the morning, & post the results...

Thanks again for your time...

---

### Post by handy on 2006-09-29
Unfortunately it did not?

I have the same 2 addresses that I had before...

---

### Post by wieman01 on 2006-09-30
What does your "interfaces" file look like now? This is odd...

---

### Post by handy on 2006-09-30
> **wieman01 said:**
> What does your "interfaces" file look like now? This is odd...

See below:

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
dns-nameservers 208.67.222.222

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

---

### Post by wieman01 on 2006-09-30
Would you want to try Static IP rather than DHCP? Perhaps that changes things... Worth a try.

---

### Post by handy on 2006-09-30
I just checked my networking settings & found that the router's IP address has been written in at the top of the list again?

I checked this morning & it was not there.   The machine has not been rebooted, but now it is there again :rolleyes: 

Got me stumped. ](*,) 

I think I'll just make the **/etc/resolv.conf** *immutable* again.  That works for me.

I have wasted too much time on this problem.  There have been so many answers, only one work around & no **true** fix for the problem, it is still not truely understood...

This problem was beaten in Breezy, but has beaten me in Dapper.
I will take up the fight again after Edgy is released, if need be.

Thanks to all concerned for your time & effort... :KS

---

### Post by wieman01 on 2006-09-30
Hi Handy, 

Ok... Your workaround being this one, right?
> sudo chmod -w-w-w /etc/resolv.conf 
Just to close this issue.

---

### Post by mips on 2006-09-30
[http://www.ubuntuforums.org/showthread.php?t=128254](http://www.ubuntuforums.org/showthread.php?t=128254)  post#13
[http://www.ubuntuforums.org/showthread.php?t=126533](http://www.ubuntuforums.org/showthread.php?t=126533)  post#17

---

### Post by handy on 2006-09-30
@**Wieman01** The following worked for ***me***:

**chattr +i /etc/resolv.conf**

use

**chattr -i /etc/resolv.conf**

to undo, so you can edit it.

That said.

@**Mips** Thanks for your input mips, the info from here:

[http://www.ubuntuforums.org/showthread.php?t=126533](http://www.ubuntuforums.org/showthread.php?t=126533)

Is what I used in Breezy, (doesn't work in Dapper) I got it from this location:

[http://www.ubuntuforums.org/showthread.php?t=11544&highlight=d-link+adsl+router](http://www.ubuntuforums.org/showthread.php?t=11544&highlight=d-link+adsl+router) post# 2

The first link you offered:

[http://www.ubuntuforums.org/showthread.php?t=128254](http://www.ubuntuforums.org/showthread.php?t=128254) post# 13

looks interesting, I'll play with those options & see...

It really looks like this problem is caused by cheap routers :(

---

### Post by handy on 2006-09-30
After following **option 3** from [http://www.ubuntuforums.org/showthread.php?t=128254&page=2](http://www.ubuntuforums.org/showthread.php?t=128254&page=2) Post# 13. 

I cleared the **/etc/resolv.conf** & brought the interface down and up again:

[B]sudo ifdown eth0
sudo ifup eth0[/B]

I have at last got the desired result!: 

***The correct DNS addresses, in the correct order & with the router's IP address at the bottom!*** 

Long may it last...

Thanks again for the link Mips! :KS

---

### Post by mips on 2006-10-01
> **handy said:**
> A
Thanks again for the link Mips! :KS

No problem. The truth is out there. You just have to look for it ;)

---

### Post by handy on 2006-10-01
> **mips said:**
> No problem. The truth is out there. You just have to look for it ;)

I know... Sometimes I get tired of digging :)

---

### Post by zvacet on 2006-10-19
Try download rp-pppoe.Thet will fix all your problems about networking,and nameservers.

---

### Post by handy on 2006-10-20
> **zvacet said:**
> Try download rp-pppoe.Thet will fix all your problems about networking,and nameservers.

I use PPPOA!

& adding the following line 

**prepend domain-name-servers 144.140.71.16, 144.140.71.30;**

(Swap your DNS addresses for mine)

to the

**/etc/dhcp3/dhclient.conf**

really is the solution for me.

[If anyone needs a walk-through for the above go here]("http://ubuntuforums.org/showthread.php?t=282034").

---

### Post by OmahaVike on 2007-07-12
FYI - this worked for me (dapper).  Thanks for the guidance!  

> **Free_As_In_Freedom said:**
> It didn't work for me because that *!@ file (enable-updates) was back again at every boot.](*,) 
The real working solution (to me of course), without messing up or deleting files or uninstalling packages was doing this (after a little man resolvconf): 
```
sudo cp /etc/resolvconf/resolv.conf.d/original /etc/resolvconf/resolv.conf.d/tail
```
before doing this, would be better to check if your "/etc/resolvconf/resolv.conf.d/original" already contains your static nameserver IP address (nameserver xxx.xxx.xxx.xxx); in other words if you put a string with "nameserver xxx.xxx.xxx.xxx" (replace x's with your nameserver's IP) on the empty "/etc/resolvconf/resolv.conf.d/tail" your baby will remember that address at every boot (well it worked for my dapper anyway) :D
Hope it will be helpful. :)

---

### Post by belgrave on 2007-11-23
same problems here....finally found a solve at:

[http://www.deepnerd.com/node/93](http://www.deepnerd.com/node/93)

---

### Post by 3ntity on 2008-06-12
> **Free_As_In_Freedom said:**
> It didn't work for me because that *!@ file (enable-updates) was back again at every boot.](*,) 
The real working solution (to me of course), without messing up or deleting files or uninstalling packages was doing this (after a little man resolvconf): 
```
sudo cp /etc/resolvconf/resolv.conf.d/original /etc/resolvconf/resolv.conf.d/tail
```
before doing this, would be better to check if your "/etc/resolvconf/resolv.conf.d/original" already contains your static nameserver IP address (nameserver xxx.xxx.xxx.xxx); in other words if you put a string with "nameserver xxx.xxx.xxx.xxx" (replace x's with your nameserver's IP) on the empty "/etc/resolvconf/resolv.conf.d/tail" your baby will remember that address at every boot (well it worked for my dapper anyway) :D
Hope it will be helpful. :)
Thx, this seems to have finally solved the issue for me, nearly 2 years after your post xD :) [This after A LOT of searching and messing about...]

Whenever I tried sudo chattr +i /etc/resolv.conf, I'd get:
```
chattr: Inappropriate ioctl for device while reading flags on /etc/resolv.conf
```

---

