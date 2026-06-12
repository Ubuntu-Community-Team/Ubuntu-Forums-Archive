---
title: "Catalyst 13.01 Legacy on Ubuntu 12.04 and Dedicated ATI Series 4500/5100"
date: 2013-02-22
forum: Multimedia Software
---

### Post by 1grouchy on 2013-02-22
I'm a little bit confused. 

This is my laptop ([**here**]("http://www.emag.ro/notebook_laptop/notebook-toshiba-satellite-l500-1xz-intel-174-coretm-i3-330m-213ghz-4gb-320gb-ati-radeon-hd5145-512mb-steel-gray--pL500-1XZ-PSLJHE-002002R3"))

I installed yesterday Ubuntu 12.04 (before I was on 11.10) and problem is overheating of GPU with open source drivers. On 11.10 I solved that with installing propietary driver from additional. But I can see that on 12.04 is not same (nothing in additional).

Tried regular solution:

> sudo apt-get install fglrx fglrx-amdcccle

sudo aticonfig --initial

with no luck. So now remove fglrx completely and back to the begining.

Now I wanna try [**this**]("http://ubuntuforums.org/showthread.php?t=1930450")

On [**this**]("http://wiki.cchtml.com/index.php/Hardware") page I can see that "Older RadeonHD (Catalyst Legacy 13.1 & Open Source)" is supporting my GPU but "MUST use a kernel <= 3.4 and Xserver <= 1.12".

So is anyone tried this maybe?

Regards.

---

### Post by 1grouchy on 2013-02-24
The other solution didn't worked also. On this forum I can't find anything by now about my GPU and this problem.

From Google I found a similar problem but its Fedora. They mention some **patch for kernel 3.4 and 3.5**. Not sure if I can post a link here, so I will not.

Basically, they talk about patching the **rpmfusion and kmod-catalyst packages**. Don't have any idea about what they mean by that.

Do someone maybe knows is there any patch for catalyst and Ubuntu 12.04 with kernel 3.5?

To describe a problem with open source driver a little bit.

**Graphic card is:**
The AMD ATI Mobility Radeon HD 5145 (renamed Mobility Radeon HD 4570) with slightly higher clock rates. Supporting HyperMemory.

**Problem:**
Regular CPU temperature with a proper driver is 46-65 C, with open source 75-90+ C when laptop shutdown itself.
Lm-sensors does not offer me monitoring GPU temp, but its clear that the driver is a problem because exactly the same situation I have on Ubuntu 11.10 and always solving it with a Catalyst driver installation.

---

### Post by elliotn on 2013-02-24
Google linqorix kernel and fglrx legacy, I can't remember but there is a repo for the linqorix kernel and a special modified ATI driver for the legacy devies, I also use it

---

### Post by Yellow Pasque on 2013-02-24
> with no luck
Please elaborate. Why didn't the regular fglrx package work?

---

### Post by elliotn on 2013-02-25
[http:// https://launchpad.net/~makson96/+archive/fglrx]("http:// https://launchpad.net/~makson96/+archive/fglrx")

here everything explain

---

### Post by Yellow Pasque on 2013-02-25
No, the makson PPA is only to downgrade Xserver on Ubuntu 12.10. It does not have any packages for Ubuntu 12.04/Precise.

---

### Post by 1grouchy on 2013-02-25
First:
I installed 11.10 again because of work (freelance). I need computer all the time and with 12.04 currently it's not possible to manage my tasks.

Don't want to give up from 12.04 of course. I will install it soon as dual boot and then continue with a tuning fglrx driver.

**@elliotn**
Found [**[COLOR="red"]this[/COLOR]**]("http://www.webupd8.org/2011/03/how-to-install-liquorix-kernel-in.html") but it's the old article, also [**[COLOR="Red"]this[/COLOR]**]("http://askubuntu.com/questions/218382/installing-the-liquorix-kernel-on-ubuntu-12-04-x64bit") but no fglrx explanation.

I will search more to inform myself about this.


**@Temüjin**
> No, the makson PPA is only to downgrade Xserver on Ubuntu 12.10. It does not have any packages for Ubuntu 12.04/Precise.

You're right. I tried this already, in the last step, *install fglrx* I got error: there is no that package in repo.


> Please elaborate. Why didn't the regular fglrx package work?

I will elaborate when I install 12.04 again, maybe even tonight. In short, experience was overheating also. I tried too many potential solutions by now and can't remember the details about this case, sorry. 

Every "solution" was tried on fresh installed system, to be clear, so there was no chance for some kind of driver conflict.

_Is there any output that you need from system?_ I will post it here on forum to help you diagnosing the problem.


Basically, my next idea (if open source driver fail again) is to install 3.4 kernel which I found [**[COLOR="red"]here[/COLOR]**]("http://www.n00bsonubuntu.net/content/linux-kernel-v3-4-rc3-precise-is-released/") and try [**[COLOR="red"]this[/COLOR]**]("http://askubuntu.com/questions/124292/what-is-the-correct-way-to-install-ati-catalyst-video-drivers-fglrx/126513#126513") with catalyst 13.1 [**[COLOR="red"]legacy[/COLOR]**]("http://support.amd.com/us/gpudownload/linux/legacy/Pages/legacy-radeon_linux.aspx").

One thing confusing me a little bit. [**[COLOR="red"]This[/COLOR]**]("http://www.ubuntubuzz.com/2012/05/install-kernel-340-stable-on-ubuntu.html") article where guy says at the end.
[SIZE="2"][COLOR="DimGray"]Warning: Install kernel 3.4 at your own risk! as version 3.4 is not supported for 12.04 LTS release. Before restarting your system, make sure you re-install your system device drivers (graphics card, sound cards, wireless cards, etc.).[/COLOR][/SIZE]


So is it supported by 12.04 now? And what do you think about solution above?

Tnx guys, regards!

---

### Post by 1grouchy on 2013-04-23
To close this thread down.

I gave up.. There is no driver that is working on 12.04 and this bloody GPU Hybrid system. 


- **Basic which comes with Ubuntu 12.04:** CPU temp 75 - 90, shutdowns
- **Fglrx binary:** After reboot, Ubuntu starts in minimal mode, catalyst is not working, it says that is wrong driver for GPU
- **Manual instalation of Catalyst 13.01 for old cards:** CPU temp 75 -90, shutdowns


Can't belive what is going on. Laptop 2 years old and without driver support.

---

### Post by delcypher on 2013-07-16
For what it's worth I managed to get the catalyst 13.1 (fglrx version 8.97.2) legacy driver working on Ubuntu Linux 12.04 on kernel version 3.6.0 (my card is Radeon HD4870 ) and X server 1.11.3 by using some patches used in the Arch Linux AUR version of the legacy catalyst driver.

Here are the steps roughly...

1. Remove any old catalyst driver you have installed
2. Download the latest (at the time writing) catalyst driver and extract
```

$ wget http://www2.ati.com/drivers/legacy/amd-driver-installer-catalyst-13.1-legacy-linux-x86.x86_64.zip
$ unzip amd-driver-installer-catalyst-13.1-legacy-linux-x86.x86_64.zip
$ chmod u+x ./amd-driver-installer-catalyst-13.1-legacy-linux-x86.x86_64.run 
$ ./amd-driver-installer-catalyst-13.1-legacy-linux-x86.x86_64.run --extract fglrx_temp

```
3. Download the catalyst-total-hd234k Arch Linux AUR package tarball (we'll take some patches from it) and extract
```

$ wget https://aur.archlinux.org/packages/ca/catalyst-total-hd234k/catalyst-total-hd234k.tar.gz
$ tar -xvf catalyst-total-hd234k.tar.gz

```
4. Apply two patches so the fglrx kernel module will build against the 3.6.0 kernel
```

$ cd fglrx_temp
$ patch -p1 -i ../catalyst-total-hd234k/3.5-do_mmap.patch
$ patch -p1 -i ../catalyst-total-hd234k/makefile_compat.patch

```
These patches should apply cleanly. If they don't THEN STOP!
5. Build the packages
```

$ ./ati-installer.sh 8.970 --buildpkg Ubuntu/precise

```
6. Install the packages
```

$ cd ../
$ sudo dpkg -i fglrx_8.970-0ubuntu1_amd64.deb  fglrx-amdcccle_8.970-0ubuntu1_amd64.deb  fglrx-dev_8.970-0ubuntu1_amd64.deb

```
Be aware of any error messages!
7. [OPTIONAL] Mark the packages as held (so we don't accidently upgrade them).
```

$ sudo aptitude hold fglrx fglrx-amdcccle fglrx-dev

```
8. Kill X 
```

$ sudo stop gdm

```
9. Initialise X configuration
```

$ sudo aticonfig --initial
$ sudo touch /etc/X11/xorg.conf-special

```
10. Reboot

---

### Post by Joni_Nevalainen on 2014-02-11
[TABLE]
[TR]
[TD="class: answercell"]                  On my T400 laptop, the ATI mobility radeon graphics card has become unsupported by the latest 13.10 fglrx driver.

  ```
(II) Module fglrx: vendor="FireGL - AMD Technologies Inc."
   compiled for 1.4.99.906, module version = 13.10.10

$ lspci | grep VGA
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RV620/M82 [Mobility Radeon HD 3450/3470]
$ lspci -n | grep 01:00.0
01:00.0 0300: 1002:95c4
```
  The /var/log/Xorg.0.log shows this line:```
(EE) No supported AMD display adapters were found

```
Fixed by downgrading and locking the fglrx package with synaptic manager: [http://www.howtogeek.com/117929/how-to-downgrade-packages-on-ubuntu/](http://www.howtogeek.com/117929/how-to-downgrade-packages-on-ubuntu/)
  As text:
  
[LIST=1]
[*]start synaptic 
[*]search for the fglrx package 
[*]choose menu Package -> force version 
[*]after selecting the earlier version, click apply 
[*]choose menu Package -> lock version 
[/LIST]
  Now Steam on Linux works again too.
      
     [TABLE="class: fw"]
[TR]
[TD="class: vt"] [share]("http://askubuntu.com/a/418917/13451")[edit]("http://askubuntu.com/posts/418917/edit")[delete]("http://askubuntu.com/questions/345530/how-can-i-install-ati-catalyst-video-driver-of-ubuntu-12-04-3/418917#")[flag]("http://askubuntu.com/questions/345530/how-can-i-install-ati-catalyst-video-driver-of-ubuntu-12-04-3/418917#")[/TD]
[TD="class: post-signature, align: right"]                               answered 22 hours ago     
              [URL="http://askubuntu.com/users/13451/joni-nevalainen"][IMG]https://www.gravatar.com/avatar/b36ce62c26858176db48dfb043694d55?s=32&d=identicon&r=PG[/IMG]
[/URL]     
              [Joni Nevalainen]("http://askubuntu.com/users/13451/joni-nevalainen")
        42423[/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]

---

