---
title: "/etc/tmp directory for saving flash videos"
date: 2010-10-25
forum: Multimedia Software
---

### Post by konsta82 on 2010-10-25
I used to save videos I watch on internet by copying them from /etc/tmp folder on all previous versions. But,it's not working on maverick.
Are temp video files being saved somewhere else or what ???

---

### Post by konsta82 on 2010-10-25
It is only /tmp , I'm sorry for error

---

### Post by sleepee on 2010-10-26
according to omgubuntu.co.uk maverick uses the new flash version that changes the folder where the flash files are located...  apparently it uses ~/.mozilla/firefox/userprofile/cache now.

[http://www.omgubuntu.co.uk/2010/09/saving-flash-videos-in-linux-tmp-no-longer-works/](http://www.omgubuntu.co.uk/2010/09/saving-flash-videos-in-linux-tmp-no-longer-works/)

i still can't find them, but maybe you'll have better luck?

---

### Post by clickwir on 2010-10-26
I haven't found them either since the upgrade. I installed the YouTube One Click Downloaded addon for Firefox instead. 

I'm assuming it's a change Adobe did to flash to make things harder to copy. Maybe a baby step attempt at TRYING to get more copyright holders to be ok with allowing Linux users.

---

### Post by lisati on 2010-10-26
> **clickwir said:**
> I haven't found them either since the upgrade. I installed the [COLOR="Red"]YouTube One Click Downloaded addon[/COLOR] for Firefox instead. 


Please see the link in my sig.

---

### Post by clickwir on 2010-10-26
> **lisati said:**
> Please see the link in my sig.

I know and respect what you are getting at. I'm just trying to help get through the mass of unanswered questions and help make users appreciate Ubuntu and how great the forums could be.

We don't want to sound like Microsoft around here. Lets try to help people more! :)

---

### Post by sisco311 on 2010-10-26
I would try something like:
```
find ~/.[a-z]* -type f | while read file; do if [[ $(file -b $file) = "Macromedia Flash Video" ]]; then echo $file; fi; done
```
or:
```
find ~/.mozilla -type f | while read file; do if [[ $(file -b $file) = "Macromedia Flash Video" ]]; then echo $file; fi; done
```
to locate the flash files.

---

### Post by lisati on 2010-10-26
> **clickwir said:**
> I know and respect what you are getting at. I'm just trying to help get through the mass of unanswered questions and help make users appreciate Ubuntu and how great the forums could be.

We don't want to sound like Microsoft around here. Lets try to help people more! :)

That's ok, nothing personal intended.

---

### Post by taumau on 2011-01-14
...

---

### Post by taumau on 2011-01-14
...

---

### Post by taumau on 2011-01-14
I´m using Google Chrome and I´ve copy the temporary file in the /tmp folder.

But what file type is this?
It has no file extension.

Thank you

---

### Post by AggravatedGestalt on 2011-02-23
> **sisco311 said:**
> I would try something like:
```
find ~/.[a-z]* -type f | while read file; do if [[ $(file -b $file) = "Macromedia Flash Video" ]]; then echo $file; fi; done
```or:
```
find ~/.mozilla -type f | while read file; do if [[ $(file -b $file) = "Macromedia Flash Video" ]]; then echo $file; fi; done
```to locate the flash files.

I get "Permission denied" running the first with either sudo, or standard user. I do not like this gvfs stuff. Who to blame; GNOME, Canonical, or my own ignorance of how to defeat this odd restriction of root?  

The second command however, worked beautifully, and guided me right to where all those flash files were hiding: /home/"myUserName"/.mozilla/firefox/kjydlve3.default/Cache/

It was easy from there, with all the flash files showing as film reel icons. Mucho Gracias for the excellent search command! Not as convenient as going to the old /tmp, but surely a script could be quickly written to basically mv flash* /home, or something, with a single click.

---

### Post by chetancrasta on 2011-02-24
While you can get the flash videos from firefox's cache, it is not as convenient and reliable as getting it from the /tmp directory.

Therefore, if you want to restore this 'feature', you will need to downgrade Flash to version 10.1.102.64

The download link for older versions of flash is [http://kb2.adobe.com/cps/142/tn_14266.html](http://kb2.adobe.com/cps/142/tn_14266.html)

Download the (large) file named "Flash Player 10.1.102.64 and 9.0.289.0".
After downloading, extract the file named flashplayer10_1r102_64_linux.tar.gz

From this file extract libflashplayer.so and overwrite the file at /usr/lib/flashplugin-installer (you will need root privileges, try gksudo nautilus)

Restart Firefox and your flash videos will land up in the /tmp directory as before! This won't work for Google Chrome, it will continue to use the latest version of Flash.

Note: For the above steps to work, a version of Adobe Flash should have been previously installed.

---

### Post by TeoBigusGeekus on 2011-02-24
See my posts in [this]("http://ubuntuforums.org/showthread.php?t=1688948") thread.

---

### Post by luigi_mb on 2011-02-24
> **taumau said:**
> I´m using Google Chrome and I´ve copy the temporary file in the /tmp folder.

But what file type is this?
It has no file extension.

Thank you

```

file [cache item]

```


/luigi

---

### Post by chetancrasta on 2011-02-25
BTW, the latest version of Flash (10.2) is a feature update, not a security update. Therefore, one can safely use Flash 10.1 as long as no security bug has been discovered in it.
Google Chrome uses a different flash plugin file, therefore the steps I described earlier works only for Firefox.

---

### Post by chetancrasta on 2011-04-10
Here is script that makes downloading flash videos even easier than copying it from /tmp: [http://davesource.com/Solutions/2011...ash-files.html](http://davesource.com/Solutions/2011...ash-files.html)
This technique is better than downgrading Flash because older versions of Flash have security vulnerabilities.

---

