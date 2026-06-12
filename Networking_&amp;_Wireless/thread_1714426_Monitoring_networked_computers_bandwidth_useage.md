---
title: "Monitoring networked computers bandwidth useage"
date: 2011-03-25
forum: Networking &amp; Wireless
---

### Post by kb1uab on 2011-03-25
I hope someone can help me with finding an application to suit my needs. Back in school I remember using an application that would identify active IP addresses on a network, and basically show you a log of activity. We actually monitored another lab and went in and showed them what we saw (all the machines had IP addresses on the monitors.) We could see websites, bandwidth, etc.

I'm trying to find an application that would do this again. I've been trying to monitor my networks to see what machines are performing unauthorized operations. ISP is showing high bandwidth usage and there is no way checking email and browsing is using this amount, 200GB a month! Something is going on here.

Please help!

---

### Post by josephmills on 2011-03-25
hi there I am new to linux but there are a boat load of programs that do what you are talking about here is a list of some of them 
ipcop
autoscan 
nmap
aircrack-ng 
I like aircrack my self 
but could you post ```
lspci
```

---

### Post by josephmills on 2011-03-25
I forgot about wireshark

---

### Post by josephmills on 2011-03-25
also if you think that you machine has been zombiefide then try ```
top 
```are there any programs running that shouldn't be?

---

### Post by kb1uab on 2011-03-25
Joseph,

Thanks for the reply. I am also new to linux and finding solutions can be a painstaking process.

I have linux servers supporting a Windows network, and I fear that a machine in either network might have a cold. I don't have solid skills of CLI, but I am working on it, so any help you can offer would be greatly appreciated. I don't think the problem is in an Ubuntu machine, as they were setup and are running fine. It would be nice to have them keeping tabs on the networks so I know whats going on. I will work with your suggestions and post my findings.

I did run the two you listed - top and lspci

top is showing me process usage, nothing strange going on here. Appears to be what is running, nothing extra

lspci is showing active hardware, nothing extra

Whats aircrack going to do for me? I'm looking to see whats going on with the wired machines, will aircrack monitor the wireless connections?

---

### Post by josephmills on 2011-03-25
> 

Whats aircrack going to do for me? I'm looking to see whats going on with the wired machines, will aircrack monitor the wireless connections?

yes it will and others(networks). if your wireless card can go into moniter mode post ```
lspci
``` and we can tell if can. Also autoscan is awesome its gui based.If you go to [http://autoscan-network.com/download/](http://autoscan-network.com/download/) you can get auto scan. download, run and let the wizard take care of the rest. Real easy to use. 
Aircrack-ng is based in the CLI. So is nmap but the is zenmap which is a gui for nmap. Wireshark is a gui to and is fairly easy to run.

---

### Post by josephmills on 2011-03-25
if you really want to you could always run backtrack 4 r2 as a live cd and that has all of the programs in it that I listed above [http://www.backtrack-linux.org/downloads/](http://www.backtrack-linux.org/downloads/)

---

### Post by kb1uab on 2011-03-30
I have a machine at home running backtrack. I haven't had time to really sit down and hammer on it. The most I did was compile a driver for a wireless device I have. It worked out great. Any insight you have on this subject would be greatly appreciated, either in here or in a private message so its easy to keep track.

Again, Thanks a bunch!
Wayne

---

