---
title: "Easy Internet connection sharing with firestarter."
date: 2009-10-16
forum: Networking &amp; Wireless
---

### Post by weirdtalk on 2009-10-16
So I wanted to hook up a windows laptop to the internet this way:


internet -> wireless (wlan0) -> linux desktop -> wired (eth0) -> windows laptop

and found this [guide]("https://help.ubuntu.com/community/Internet/ConnectionSharing")

but wanted to use a easier way. Well I found it after some effort, so I thought I'd post how I did it.

first install firestarter
```
sudo apt-get install firestarter
```

then give your wired connection a ip

```
sudo ifconfig eth0 address 192.168.1.1
```

(I did this because firestarter would give me an error about eth0 not being ready)

(I choose 192.168.1.1 because I was going to use 192.168.0.1, but when I did I couldn't use the internet, the cause: my modem is 192.168.0.1, the solution: use something else)

run firestarter
```
sudo firestarter
```

run the wizard. first choose wlan0 and dhcp. click next choose eth0. next. save.

Now set up the laptop.
(connect it with either a crossover cable or connect the desktop and laptop to a switch)
in windows go to the network connection properties.
under tcp/ip properties set to manual.
ip of 196.168.1.2
gateway of 192.168.1.1
mask of 255.255.255
dns primary of 208.67.222.222
secondary of 208.67.220.220


and now you should be set up.
comments welcome.

---

### Post by BlackRockCity on 2009-10-27
I found that I had to assign the IP to eth0 using:

```
 sudo ifconfig eth0 192.168.1.1
```That got rid of the error saying my eth0 was not ready. But now I get a more general error.

---

