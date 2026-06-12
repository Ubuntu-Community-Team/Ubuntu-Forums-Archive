---
title: "Setup PPPoE"
date: 2010-12-01
forum: Networking &amp; Wireless
---

### Post by friendishan on 2010-12-01
Hi,

I have to setup PPPoE on ubuntu which requires only username and pass to login.

If it's some graphic software , i'll be happy :P

as for pppoeconf.. it gives me error some modconf not found.

I currently have 10.04 installed and would like to update it after getting the internet working :-| .

I won't be able to connect to internet in ubuntu so please don't tell me methods which will require me to access internet IN ubuntu. If some downloading from windows is required it's good.

Thank You!

---

### Post by dineshs on 2010-12-01
Try
[http://ubuntuforums.org/showpost.php?p=9611450&postcount=2](http://ubuntuforums.org/showpost.php?p=9611450&postcount=2)
If you find any difficulty pl post the output of```
sudo lshw -C network
```when the cable is plugged

---

### Post by friendishan on 2010-12-01
problem faced:- It says No devices found or something like that. No options for connecting. ( I created the DSL Connection 1 )

```
ishan@ishan-desktop:~$ sudo lshw -C network
[sudo] password for ishan: 
  *-network UNCLAIMED     
       description: Ethernet controller
       product: AR8151 v1.0 Gigabit Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:02:00.0
       version: c0
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list
       configuration: latency=0
       resources: memory:fdec0000-fdefffff ioport:df00(size=128)
ishan@ishan-desktop:~$
```

---

### Post by dineshs on 2010-12-01
>  *-network UNCLAIMED     
       description: Ethernet controller
       product: AR8151 v1.0 Gigabit Ethernet
Network unclaimed is not a good sign.Please see[ this]("http://ubuntuforums.org/showthread.php?t=1555540&highlight=build-essential")

---

### Post by friendishan on 2010-12-01
Can this problem be overcome by a fresh install of ubuntu 10.10 without hassles ? 

PS:- I'm a noob at all this :-|

---

### Post by dineshs on 2010-12-01
> **friendishan said:**
> Can this problem be overcome by a fresh install of ubuntu 10.10 without hassles ? 
PS:- I'm a noob at all this :-|
I am not an expert.My suggestion is try a live CD first.

---

### Post by friendishan on 2010-12-01
[http://partner.atheros.com/Download.aspx?id=125](http://partner.atheros.com/Download.aspx?id=125) unable to download this. 

After clicked on Accept... it just returns to that page. :(

---

### Post by dineshs on 2010-12-01
What happens when you click the link BACK TO DRIVER DOWNLOADS at the top of the page ?

---

### Post by friendishan on 2010-12-02
I am sent to this page [http://partner.atheros.com/Drivers.aspx](http://partner.atheros.com/Drivers.aspx)

---

### Post by dineshs on 2010-12-03
Now download 
> AR81Family Linux Driver
AR81Family-linux-v1.0.1.14.tar.gz	137K
and follow postcount #7 in 
[http://ubuntuforums.org/showthread.php?t=1555540&highlight=build-essential](http://ubuntuforums.org/showthread.php?t=1555540&highlight=build-essential)

---

