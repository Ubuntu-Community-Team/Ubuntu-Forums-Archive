---
title: "Again with this Flash update"
date: 2013-02-13
forum: Multimedia Software
---

### Post by augoldfinger on 2013-02-13
Well everytime I do a flash update FF will not work with videos like youtube.
It seems as though it's at least an hour searching on the web for an answer. This time I cant figure it out.

I have flash aid... didn't help & mostley doesnt anymore...
When I first downloaded it it was great... But now, not so much

I'm getting very frustrated with these updates

My new error message is 
*"E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem." *

I'm using Kubuntu 12.04

Thanks all
Much appreciated!

---

### Post by pqwoerituytrueiwoq on 2013-02-13
give this a try:
```
sudo dpkg --configure -a
```since that is what it said to do
```
sudo sed -i 's/\# deb h/deb h/;s/\# deb-src h/deb-src h/' /etc/apt/sources.list;sudo apt-get update;sudo apt-get purge flashplugin-installer adobe-flash*;sudo apt-get install adobe-flashplugin adobe-flash-properties-kde
```enables Canonical Partners repo, update the apt database, purges all flash, and install flash

for non kubuntu users change kde to gtk at the end of the line

---

### Post by augoldfinger on 2013-02-13
> **pqwoerituytrueiwoq said:**
> give this a try:
```
sudo dpkg --configure -a
```since that is what it said to do
```
sudo sed -i 's/\# deb h/deb h/;s/\# deb-src h/deb-src h/' /etc/apt/sources.list;sudo apt-get update;sudo apt-get purge flashplugin-installer adobe-flash*;sudo apt-get install adobe-flashplugin adobe-flash-properties-kde
```enables Canonical Partners repo, update the apt database, purges all flash, and install flash

for non kubuntu users change kde to gtk at the end of the line

Hey Thanks!

That put a window in my terminal I cant seem to get past
*"TrueType core fonts for the Web EULA"* 

It says "OK" at the bottom of terminal, but nothing happens when I hit enter :confused:

---

### Post by pqwoerituytrueiwoq on 2013-02-13
what did you do before this happened this issue is not a flash one
is there nothing you can tab to and hit enter?

---

### Post by schragge on 2013-02-13
I guess there's some checkbox on that EULA dialog window that need to be checked to proceed, like *I've read all this and am agree with it*.

---

### Post by shantiq on 2013-02-13
[attach]231377[/attach]




sorry by the way schragge was not the original asker but I leave the image here as a guide anyway :)

---

### Post by augoldfinger on 2013-02-13
> **pqwoerituytrueiwoq said:**
> what did you do before this happened this issue is not a flash one
is there nothing you can tab to and hit enter?

Thanks again

Tab enter... did the trick
You know I use to use DOS & never thought of that

Downloading now
I'll report back

Thanks

> **shantiq said:**
> [attach]231377[/attach]




sorry by the way schragge was not the original asker but I leave the image here as a guide anyway :)

You're right bud, Thanks I did not understand

---

### Post by speartip on 2013-02-13
>   It says "OK" at the bottom of terminal, but nothing happens when I hit enter :confused:

Try using your arrow keys until the "OK" is highlighted then hit enter.

---

### Post by augoldfinger on 2013-02-13
Thanks guy's ):P
Worked great
Now to update my other three computers

---

