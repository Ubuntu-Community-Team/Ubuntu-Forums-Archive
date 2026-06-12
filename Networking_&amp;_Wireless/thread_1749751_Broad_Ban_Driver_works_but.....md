---
title: "Broad Ban Driver works but...."
date: 2011-05-04
forum: Networking &amp; Wireless
---

### Post by orbitpilot on 2011-05-04
when i click the internet connenction dropdown in the top right, "wireless connection" doesnt even show up anymore.

---

### Post by josephmills on 2011-05-04
please open up your terminal and type in 
```

lspci -nn 

```
then 
```

rfkill list all 

```
this last one takes a while to load 
```

sudo lshw -c network 

```
[b]
please copy and paste all here 
[/b]
thanks

---

### Post by orbitpilot on 2011-05-04
> **josephmills said:**
> please open up your terminal and type in 
```

lspci -nn 

```
then 
```

rfkill list all 

```
this last one takes a while to load 
```

sudo lshw -c network 

```
[b]
please copy and paste all here 
[/b]


Alright, im running from vista right now so i cant paste into here. but i can upload the file (which i did) it is attached [here.]("http://www.mediafire.com/?fhxylfn03ydapda")
thanks

---

### Post by josephmills on 2011-05-04
make sure that you are connected to the net via cat5 (ethernet)if you dont have it then please go no further and tell us thanks. but if you do please plug in and open your terminal and type in 
```

sudo apt-get install b43-fwcutter

```
then 
```

sudo apt-get install firmware-b43-installer

```
then 
```

sudo apt-get install bcmwl-kernel-source

```
then 
```

sudo apt-get update 

```
then 
```

sudo apt-get upgrade 

```
press y when it asks 
then 
```

sudo reboot 

```
after reboot please

---

### Post by chili555 on 2011-05-04
> sudo lshw -c networkIt's actually C not c.

---

### Post by josephmills on 2011-05-04
If you have no router and are on wireless only do this 
please click on this link it will download you firmware and driver 
[http://www.omattos.com/sites/default/files/b43-all-fw.tar_.gz](http://www.omattos.com/sites/default/files/b43-all-fw.tar_.gz)
then after you downloaded it move it to you 
[b]
home folder
[/b]
then right click on your on your home folder 
[b]
not
[/b]
your download. now you want to 
[b]
create a folder
[/b] 
called 
[b]
wireless
[/b] then put the download in the folder. After that go back to your terminal and type in 
```

sudo cp -r ~/wireless/* /lib/firmware/ 

``` 
then 
```

cd /lib/firmware

```
then 
```

sudo -s 

```
then 
```

tar -xzf b43-all-fw.tar_.gz

``` then 
```

exit

```
then 
```

sudo reboot 

```
tell us how it all works out

---

### Post by josephmills on 2011-05-04
> **chili555 said:**
> It's actually C not c.

I thought that they both did the same thing. Am I wrong?

---

### Post by orbitpilot on 2011-05-04
> **chili555 said:**
> It's actually C not c.

oh really?
Does it make a difference? ill see

anyways. that got me no where. still no "wireless connectionS" in dropdown.

---

### Post by josephmills on 2011-05-04
> **orbitpilot said:**
> oh really?
Does it make a difference? ill see

anyways. that got me no where. still no "wireless connectionS" in dropdown.

read it carefully I have the same card if the first dont help try the second one

---

### Post by orbitpilot on 2011-05-05
> **josephmills said:**
> If you have no router and are on wireless only do this 
please click on this link it will download you firmware and driver 
[http://www.omattos.com/sites/default/files/b43-all-fw.tar_.gz](http://www.omattos.com/sites/default/files/b43-all-fw.tar_.gz)
then after you downloaded it move it to you 
[b]
home folder
[/b]
then right click on your on your home folder 
[b]
not
[/b]
your download. now you want to 
[b]
create a folder
[/b] 
called 
[b]
wireless
[/b] then put the download in the folder. After that go back to your terminal and type in 
```

sudo cp -r ~/wireless/* /lib/firmware/ 

``` 
then 
```

cd /lib/firmware

```
then 
```

sudo -s 

```
then 
```

tar -xzf b43-all-fw.tar_.gz

``` then 
```

exit

```
then 
```

sudo reboot 

```
tell us how it all works out

Alright just did it, signing in now.

Still not there.

---

### Post by orbitpilot on 2011-05-06
> **orbitpilot said:**
> Alright just did it, signing in now.

Still not there.

Anyone? BUMP


this is making me so mad.

---

