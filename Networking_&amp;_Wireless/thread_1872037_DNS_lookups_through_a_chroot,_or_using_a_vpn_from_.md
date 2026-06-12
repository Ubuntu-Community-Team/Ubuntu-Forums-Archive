---
title: "DNS lookups through a chroot, or using a vpn from inside a chroot"
date: 2011-10-29
forum: Networking &amp; Wireless
---

### Post by Dougie187 on 2011-10-29
Hi Everyone,

I have a fairly odd thing that I'm trying to do. At least, I haven't been able to find much in the way of instructions on this.

**A bit of back story (could probably skip this if you want):**
My work uses juniper's network connect for a vpn, and it only works on 32bit ubuntu with 32bit firefox and 32bit java. It has to be initiated from the web portal for it to connect to the vpn server.

This web app doesn't run under 64bit linux, even with 32bit firefox and 32bit java. At least in the manner that is required for my vpn server. I have tried almost all methods I could find online to get it to work (even mad scientist's method), and none worked.

I tested getting it to work in a 32bit virtual machine, and it worked fine.

**Now to the real problem:**
So, I decided to try to get it to work in a chroot. So, I set up a 32bit 11.10 chroot and installed 32bit java and firefox in it. And now I have it working to the point that I can run my 64bit firefox and the 32bit firefox at the same time, and connect to the VPN inside the chroot.

The only problem, for some reason I can't access the connection/dns that available inside the chroot from the host. IE, lets say I have server1 which is behind the vpn. Inside of the chroot, I can ssh into server1 just fine, but outside I get "no route to host".

I'm looking for a solution to essentially access the vpn that's available inside of the chroot from the host so I can ssh into server1. This is mainly so I can scp files easily to and from the server.

Please let me know if there is anymore information that I can provide to help.

Thanks in advance for any help.

**_UPDATE:_**
My vpn seems to update /etc/hosts and /etc/resolv.conf. If I copy the chroot (updated) versions of those to my host versions outside of the chroot, then the vpn works as expected, and I can ssh into server1 just fine.

Now I'm trying to figure out how to make the chroot edit the host's versions of those two files.

---

### Post by poolet on 2011-10-30
[SIZE=1]try to flush the dns to see what it would happen::

```
sudo aptitude install nscd 
```

```
sudo /etc/init.d/nscd restart
```

```
net ads dns register - P 
```[/SIZE]

at the end there is no dns cache on ubuntu (and linux, btw) by default.
there is no reason to install the cache (nscd) only to clean it, but reading your problem it's strange, searching on net I didn't find something similar or close to your problem so give a try with the above to see whats it will happen and we will think about if isn't works(more logically ) :D

---

### Post by Dougie187 on 2011-10-30
Thanks for the advice, but it didn't change anything for me. The error I get when trying to ssh into server1 is actually...

ssh: Could not resolve hostname server1: Name or service not known

Something else that I tried, since the vpn edited the /etc/hosts file in the chroot, I copied the changes to that file into my host /etc/hosts file (outside of the chroot). But that didn't have any effect either.

---

### Post by poolet on 2011-10-30
what kind of vpn your using?? L2TP or PPTP ?? and do you have any NAT or NAT-T drives??

---

### Post by Dougie187 on 2011-10-30
> **poolet said:**
> what kind of vpn your using?? L2TP or PPTP ?? and do you have any NAT or NAT-T drives??

I don't know what kind of vpn this is, asside from it being ssl based. It's called network connect and it's made by juniper.

On another note, I tested pinging/sshing by ip outside of the chroot with the vpn active inside the chroot, and that worked fine. So as a temporary solution, I set up an entry in ~/.ssh/config with the ip to the machine in question.

It would still be nice to get the dns stuff working though.

---

### Post by Dougie187 on 2011-10-30
Ok, here is a bit of an update. I'll probably put this in the OP just so people can see if there too.

My vpn seems to update /etc/hosts and /etc/resolv.conf. If I copy the chroot (updated) versions of those to my host versions outside of the chroot, then the vpn works as expected, and I can ssh into server1 just fine.

Now I'm trying to figure out how to make the chroot edit the host's versions of those two files.

---

### Post by SeijiSensei on 2011-10-30
Why bother updating those files?  Just freeze them permanently with the correct entries.  The simplest method for this is setting up the files the way you want then "chmod 0444 /etc/hosts /etc/resolv.conf" so they won't be changed.

---

### Post by Dougie187 on 2011-10-30
> **SeijiSensei said:**
> Why bother updating those files?  Just freeze them permanently with the correct entries.  The simplest method for this is setting up the files the way you want then "chmod 0444 /etc/hosts /etc/resolv.conf" so they won't be changed.

Well, the vpn works by adding lines, and removing lines to them. And since this is on a laptop, I felt like the entries might change, depending on where I was located. So It would be safer in that regard to leave them changeable by the system, since it sets up the files on boot (it appears).

I might be misunderstanding something, but that's just how I thought the things would work.

For now, I'm just happy it works.

Thanks for the suggestion though, I'll probably give it a shot, and see if it causes me any issues.

---

### Post by poolet on 2011-11-01
glad for your :D... networks issues are a little bit strange some time and always we are looking at the wrong direction!!!!!

---

