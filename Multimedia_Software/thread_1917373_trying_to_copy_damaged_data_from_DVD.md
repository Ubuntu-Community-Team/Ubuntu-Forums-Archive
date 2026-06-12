---
title: "trying to copy damaged data from DVD"
date: 2012-01-29
forum: Multimedia Software
---

### Post by davethewave83 on 2012-01-29
I have an old family DVD that has damaged video files. I would like to copy the files to the hard drive, ignoring the errors yet continuing to copy the file (retaining the bad data in the new file) 

I tried rsync -av source destination
but when it runs into the read error it just forfeits the entire file, moving on to the next one
.
even though there is a lot of good data still there, it doesn't maintain what it has, and I would like to know how to do that.

is there any way to do that?

---

### Post by inobe on 2012-01-29
handbrake will rip damaged media, i bared witness to this..

it may appear to be stuck, but it's not, you will notice in activity console errors such as

```
Can't seek to block 256
```

the numbers will increase until it can.

basically it will continue to rip regardless of damage.

---

### Post by wolfen69 on 2012-01-29
[http://dvdisaster.net/en/](http://dvdisaster.net/en/)

```
sudo apt-get install dvdisaster
```

---

### Post by davethewave83 on 2012-01-30
> **inobe said:**
> handbrake will rip damaged media, i bared witness to this..

it may appear to be stuck, but it's not, you will notice in activity console errors such as

```
Can't seek to block 256
```

the numbers will increase until it can.

basically it will continue to rip regardless of damage.

thanks I tried to find it, apt-get install handbrake said couldn't find package handbrake, so I ran synaptic, still couldn't find it. 

Trying to use dd but it's taking an awfully long time because of the errors.

---

### Post by wolfen69 on 2012-01-30
> **davethewave83 said:**
> thanks I tried to find it, apt-get install handbrake said couldn't find package handbrake, so I ran synaptic, still couldn't find it. 

Trying to use dd but it's taking an awfully long time because of the errors.

To install handbrake, you need to add the ppa first.
```
sudo add-apt-repository ppa:stebbins/handbrake-snapshots
```
then
```
sudo apt-get update
```
then
```
sudo apt-get install handbrake-gtk
```

---

### Post by davethewave83 on 2012-02-01
thanks! I ended up using dd which did a pretty good job but I will try handbreak too.

---

