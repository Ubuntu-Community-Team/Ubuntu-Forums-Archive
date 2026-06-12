---
title: "Active Member Directory"
date: 2010-05-10
forum: Networking &amp; Wireless
---

### Post by dhillis on 2010-05-10
Been trying out Linux at the school to determine if we want to run linux on all of the desktops for the kids next year in my computer lab.  Just upgraded from 9.10 to 10.04 and now I can't log into the active directory.  I can log in as the root and still access the internet but cannot log in through the domain.  I tried leaving the domain as well.  Was going to rejoin to see if maybe this would fix the problem but I get a LSASS Eroor 1225 (0x4C9) ERROR_CONNECTION_REFUSED - Unknown error when trying to leave.  

Also on login I get an ICEAuthority can not be updated.  

I believe it is likewise open that I have installed to allow me to join?

Any help is appreciated.  Thanks

---

### Post by yvovandoorn on 2010-05-10
It sounds like it is having a problem with the computer object in AD. When you are leaving are you putting in your credentials as follows
'/opt/likewise/bin/domainjoin-cli leave domain username' or just '/opt/likewise/bin/domainjoin-cli leave domain'.

Yvo

---

### Post by dhillis on 2010-05-11
> **yvovandoorn said:**
> It sounds like it is having a problem with the computer object in AD. When you are leaving are you putting in your credentials as follows
'/opt/likewise/bin/domainjoin-cli leave domain username' or just '/opt/likewise/bin/domainjoin-cli leave domain'.

Yvo

actually I am not leaving by command line.  When I click System/Administration/Active Membership Directory I just click on leave.  Sorry for not explaining that.  I am still new to Linux and coding in the terminal so I am really quite confused.

---

### Post by yvovandoorn on 2010-05-11
Could you try perhaps? Once you are joined, there should be no longer any command line stuff involved but it just sounds like something is munged in AD.

---

### Post by dhillis on 2010-05-12
> **yvovandoorn said:**
> It sounds like it is having a problem with the computer object in AD. When you are leaving are you putting in your credentials as follows
'/opt/likewise/bin/domainjoin-cli leave domain username' or just '/opt/likewise/bin/domainjoin-cli leave domain'.

Yvo


says the file does not exist....am I suppose to type something in front of it...sorry for my ignorance

---

### Post by yvovandoorn on 2010-05-12
That's ok, I can try to help. 

If you type in 
```
dpkg --list likewise*
```


What does it respond with?

PS, if you want you can IM me as well. Either via the MSN or AIM link to the left of my name.

---

### Post by yvovandoorn on 2010-05-12
Scratch what I just said. I just spoke to one of the devs who told me we 'normalized' for Ubuntu, meaning we install our binaries in /usr/bin.

With that said, go ahead and run the following command:

```
sudo /usr/bin/domainjoin-cli leave DOMAIN
```
Replace DOMAIN with your active directory domain name.

---

### Post by dhillis on 2010-05-13
thanks...i'll try that...i can't get back to the computer till monday because they are having the kids do end of course exams in that lab.....i'll let you know how it goes.

---

### Post by dhillis on 2010-05-18
well it ask for a domain password and I don't have those permissions...guess i'll have to talk to one of the tech guys to see what is going on...

---

