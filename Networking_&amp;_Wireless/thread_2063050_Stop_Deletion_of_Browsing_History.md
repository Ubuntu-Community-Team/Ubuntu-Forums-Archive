---
title: "Stop Deletion of Browsing History"
date: 2012-09-26
forum: Networking &amp; Wireless
---

### Post by omegamu on 2012-09-26
Hi 

For business reasons i need to find a way to stop users deleting there browsing history.

1. Is there a way to disable there deletion?

2. If not is there a way to save (real time) the browsing history to another(local) location?

3. Is there also a way to disable incognito mode?

Thanks ahead of time.

---

### Post by orange2k on 2012-09-26
There is probably a way to make a system work in kiosk mode, thus nobody be able to change settings and such, but I don't think thats what you want. But if the employees are accessing internet trough a server you can monitor their internet activity on that server...

Not sure if thats ethical though...

But if you want to prevent them visiting sites that aren't work related you could also set up a internet access policy on the server or totally disable web usage except for e-mail...

---

### Post by omegamu on 2012-09-26
First of all ethical or not there are legal reasons for this, as we own the devices.

The devices are laptops so they often travel outside the domain and use public internet so we need to keep the history without the aid of a network log.  Ergo we need a local copy that cant be deleted.

---

### Post by orange2k on 2012-09-26
> **omegamu said:**
> First of all ethical or not there are legal reasons for this, as we own the devices.

The devices are laptops so they often travel outside the domain and use public internet so we need to keep the history without the aid of a network log.  Ergo we need a local copy that cant be deleted.

In that case you need to setup each of those laptops to work in some kind of kiosk mode - something like this:
[http://www.instructables.com/id/Setting-Up-Ubuntu-as-a-Kiosk-Web-Appliance/](http://www.instructables.com/id/Setting-Up-Ubuntu-as-a-Kiosk-Web-Appliance/)

Users will not be able to change the settings and voila - you get what you want...

edit: you may be in need to deviate from the tutorial to get what you need, but still, this is a good starting point...

---

### Post by orange2k on 2012-09-26
There is also this for mozilla:

[http://kb.mozillazine.org/Locking_preferences](http://kb.mozillazine.org/Locking_preferences)

But be aware of this:

> Since it is possible to completely bypass locked preferences by running a separate version of Firefox or Mozilla Suite (or a completely different browser) from a different location, it may be necessary to restrict which programs can be run. However, at this point, it is probably a good idea to examine exactly why you are locking the preferences in the first place. If the intent is to protect users from themselves, or to keep novice users from breaking their software, then you have probably done enough. However, if you are trying to secure your network using client-side settings, then you should realize this is very difficult, and ultimately wastes too many resources. Instead, you should probably redirect your efforts to the server/router where you can fight battles that are more easily won.

---

### Post by omegamu on 2012-09-26
Thanks.

Is there other documentation on this?

---

### Post by omegamu on 2012-09-26
In that config the history is disabled? I need to keep it.

Also this disables everything but the browser i dont what this i need user to have normal access.

however if the history file in the chrome folder can be copied live (or close to) it may work.

---

### Post by orange2k on 2012-09-26
There is a way to disable deletion of browser history in Internet Explorer, but thats Windows...

[http://www.wikihow.com/Disable-Delete-Browser-History-in-Internet-Explorer](http://www.wikihow.com/Disable-Delete-Browser-History-in-Internet-Explorer)

I'm not sure you can do the same in Ubuntu without seriously finetuning what a user can do on a computer...

---

### Post by orange2k on 2012-09-26
> **omegamu said:**
> In that config the history is disabled? I need to keep it.

Also this disables everything but the browser i dont what this i need user to have normal access.

however if the history file in the chrome folder can be copied live (or close to) it may work.

Like I said that is a tutorial on how to set up a kiosk mode in general, you may need to tweak it - in your case you may need to use alternate settings, thus don't click on "clear browser history" as the tutorial suggests...):P

---

### Post by cortman on 2012-09-26
There is also [Net Responsibility]("http://netresponsibility.com/"), which emails complete browsing logs and runs as a daemon. It will alert the email recipient if it is ever shut down or bypassed, but as a daemon its presence is not obvious or noticeable.
It's what I use for accountability purposes...

---

### Post by orange2k on 2012-09-26
> **cortman said:**
> There is also [Net Responsibility]("http://netresponsibility.com/"), which emails complete browsing logs and runs as a daemon. It will alert the email recipient if it is ever shut down or bypassed, but as a daemon its presence is not obvious or noticeable.
It's what I use for accountability purposes...

This is probably the best solution by far, nice to know such programs exist...:)

---

### Post by omegamu on 2012-09-26
well besides clearing history and making chrome full screen there is only making chrome folder read only... So not much help. ;)

Question do you know a quick script that will copy a file if any changes are made and only if the file increases in size? If not thats ok just thought id ask...

---

### Post by omegamu on 2012-09-26
NR looks good.. I think this could work for me, Thanks

---

### Post by omegamu on 2012-09-26
Question: If a user is using incognito mode then the logs may not be stored and therefore not sent?

---

### Post by cortman on 2012-09-26
> **omegamu said:**
> Question: If a user is using incognito mode then the logs may not be stored and therefore not sent?

I don't think incognito mode bypasses this, but I can't be sure.

---

