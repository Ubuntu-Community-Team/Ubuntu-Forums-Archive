---
title: "Picasa error"
date: 2009-02-16
forum: Multimedia Software
---

### Post by STUMPOFWAR on 2009-02-16
I installed Picasa on my laptop. When I click on it I get the following error:
```
/dev/nvidia0 or /dev/nvidiact1 are not accesible. Picasa will crash if these files are accessible. To fix this, as root,please run:
 chmod 666 /dev/nvidia0 /dev/nvidiact1 
```

so I did....and I get:

```
seliason@Teletraan-1:~$ chmod 666 /dev/nvidia0 /dev/nvidiact1
chmod: changing permissions of `/dev/nvidia0': Operation not permitted
chmod: cannot access `/dev/nvidiact1': No such file or directory
seliason@Teletraan-1:~$ 
```

What next?

---

### Post by STUMPOFWAR on 2009-02-22
I can't find any other references to a similar problem with Picasa. I'm not sure what to do to get it to work.

---

### Post by STUMPOFWAR on 2009-02-22
duh....I cut & pasted the wrong output...... I forgot to do it as root the first time...... as root I get the same error though....

Here is the correct output:

```
root@Teletraan-1:/home/seliason# chmod 666 /dev/nvidia0 /dev/nvidiact1
chmod: cannot access `/dev/nvidiact1': No such file or directory

```

When I do them separately I get:

```

root@Teletraan-1:/home/seliason# chmod 666 /dev/nvidiact1
chmod: cannot access `/dev/nvidiact1': No such file or directory

```

so I do the other:

```
root@Teletraan-1:/home/seliason# chmod 666 /dev/nvidia0
root@Teletraan-1:/home/seliason#

``` 

Since their is no 'output' does this mean it worked or nothing happened?
When I restart the laptop and reopen Picasa I get the same error:

```
/dev/nvidia0 or /dev/nvidiact1 are not accesible. Picasa will crash if these files are accessible. To fix this, as root,please run:
 chmod 666 /dev/nvidia0 /dev/nvidiact1
```

---

### Post by xc3RnbFO8P on 2009-02-22
Use **gksu nautilus**
and change the permision from **Root** to **Teletraan-1**
in /dev/**nvidia0** and /dev/**nvidiact1**

---

### Post by STUMPOFWAR on 2009-02-22
OK....

```
seliason@Teletraan-1:~$ gksu nautilus

(gksu:10484): Gdk-WARNING **: Attempt to draw a drawable with depth 24 to a drawable with depth 32                                                              

(gksu:10484): Gdk-WARNING **: Attempt to draw a drawable with depth 24 to a drawable with depth 32

(gksu:10484): Gdk-WARNING **: Attempt to draw a drawable with depth 24 to a drawable with depth 32

(gksu:10484): Gdk-WARNING **: Attempt to draw a drawable with depth 24 to a drawable with depth 32

(gksu:10484): Gdk-WARNING **: Attempt to draw a drawable with depth 24 to a drawable with depth 32

(gksu:10484): Gdk-WARNING **: Attempt to draw a drawable with depth 24 to a drawable with depth 32

(gksu:10484): Gdk-WARNING **: Attempt to draw a drawable with depth 24 to a drawable with depth 32

(gksu:10484): Gdk-WARNING **: Attempt to draw a drawable with depth 24 to a drawable with depth 32

(gksu:10484): Gdk-WARNING **: Attempt to draw a drawable with depth 24 to a drawable with depth 32

(gksu:10484): Gdk-WARNING **: Attempt to draw a drawable with depth 24 to a drawable with depth 32
Initializing nautilus-share extension

** (nautilus:10485): WARNING **: Unable to add monitor: Operation not supported
SSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSNautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

```

Naut popped up as root. Where do I edit prefs?

I didn't run as root.....should I have

---

### Post by STUMPOFWAR on 2009-02-22
duh...sorry.....

in /dev

i don't have the option to allow  "Teletraan--1" ......but I do see "seliason"....which is my login...

I changed the permission.

---

### Post by STUMPOFWAR on 2009-02-22
Worked perfect.

Thank you for your time.

Shawn

---

### Post by xc3RnbFO8P on 2009-02-22
Glad to help

---

### Post by STUMPOFWAR on 2009-03-02
hmm.....I just opened Picasa again and I got the same error. If I go through the motions again it works.....the minute I reboot the permissions on Nvidia0 and Nvidiact1 reset to root.....

How do I make the permission change permanent?

---

### Post by STUMPOFWAR on 2009-03-04
ugh......for some reason this bug doesn't occur in KDE just Gnome......

---

### Post by STUMPOFWAR on 2009-03-10
When I got to a term I get this error.

```
seliason@Teletraan-1:~$ gksu nautilus
Initializing nautilus-clamscan extension
Initializing nautilus-share extension

** (nautilus:6600): WARNING **: Unable to add monitor: Operation not supported
SSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSNautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

```

Could this explain why the permissions on the two video files reset to root each time I reboot?

---

