---
title: "nVidia drivers - installed, but not enabled?  Need some help..."
date: 2012-01-27
forum: Multimedia Software
---

### Post by Redflea on 2012-01-27
Sony Vaio VPCCW290L
nVidia Geforce 300m series
Ubuntu 10.04 LTS

I uninstalled any/all existing nvidia using: 

sudo apt-get --purge remove nvidia-*

Then I followed the prompts below... 

```

sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get install nvidia-current
sudo apt-get install nvidia-settings
REBOOT

```

On the last line, the Settings get, it said the current settings were already installed.

I rebooted, and do not find any nvidia settings in any of the menus, and when I run jockey-text -l:

```
jockey-text -l 

kmod:nvidia_current - nvidia_current (Proprietary, Disabled, Not in use)

```

So am I running the nvidia drivers or not? And if not, how do I enable them...?

Thanks!

```
lshw

   *-display UNCLAIMED
                description: VGA compatible controller
                product: GT218 [GeForce 310M]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a2
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: latency=0
                resources: memory:e2000000-e2ffffff memory:d0000000-dfffffff memory:e0000000-e1ffffff ioport:d000(size=128) memory:e3000000-e307ffff

```

---

### Post by wolfen69 on 2012-01-27
I believe that video card is Optimus? If so, you will need to do the following: (after removing the nvidia drivers)

```
sudo add-apt-repository ppa:https://launchpad.net/~bumblebee/+archive/stable
```
then
```
sudo apt-get update
```
then
```
sudo apt-get install bumblebee bumblebee-nvidia
```
then
```
sudo usermod -a -G bumblebee $USER 
```
reboot.

---

### Post by Redflea on 2012-01-27
> **wolfen69 said:**
> I believe that video card is Optimus? If so, you will need to do the following: (after removing the nvidia drivers)

```
sudo add-apt-repository ppa:https://launchpad.net/~bumblebee/+archive/stable
```
then
```
sudo apt-get update
```
then
```
sudo apt-get install bumblebee bumblebee-nvidia
```
then
```
sudo usermod -a -G bumblebee $USER 
```
reboot.

Thanks very much...but i'm confused.  The card  is an nvidia card, what do you mean by Optimus?

---

### Post by wolfen69 on 2012-01-27
> **Redflea said:**
> The card  is an nvidia card, what do you mean by Optimus?
Optimus is a new breed of nvidia graphics that shares time with intel graphics depending on usage.

---

### Post by Redflea on 2012-01-28
> **wolfen69 said:**
> Optimus is a new breed of nvidia graphics that shares time with intel graphics depending on usage.

Thanks again...after this: 

```
sudo add-apt-repository ppa:https://launchpad.net/~bumblebee/+archive/stable
```

...getting a 404...wrong link, or ? 

Error reading [https://launchpad.net/api/1.0/~https/+archive/ppa:](https://launchpad.net/api/1.0/~https/+archive/ppa:) HTTP Error 404: Not Found
 
I do get to a valid web page when going to the https address, so the URL looks good...

[https://launchpad.net/~bumblebee/+archive/stable](https://launchpad.net/~bumblebee/+archive/stable)

But something isn't connecting properly.  Really appreciate your help.

---

### Post by Redflea on 2012-01-28
Can anyone help me with this?

There is an alternate set of install instructions here...

[https://launchpad.net/~bumblebee/+archive/stable](https://launchpad.net/~bumblebee/+archive/stable)

Somewhat confused.  :)

---

### Post by wolfen69 on 2012-01-28
Do:
```
sudo add-apt-repository ppa:bumblebee/stable
```
then
```
sudo apt-get purge nvidia-current
```
then
```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
```
then 
```
sudo apt-get install bumblebee bumblebee-nvidia
```
then
```
sudo usermod -a -G bumblebee $USER
```
reboot

---

### Post by Redflea on 2012-01-29
Thanks...really appreciate it. 

But I must be cursed...maybe time to give up. 

```
xxx@xxx:~$ sudo add-apt-repository ppa:bumblebee/stable
[sudo] password for xxx: 
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv 46C0364A882F14F899448FFCB22A95F88110A93A
gpg: requesting key 8110A93A from hkp server keyserver.ubuntu.com
gpg: key 8110A93A: public key "Launchpad PPA for Bumlebee Project" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
xxx@xxx:~$ sudo apt-get purge nvidia-current
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package nvidia-current is not installed, so not removed
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.32-33-generic linux-headers-2.6.32-33 dkms
Use 'apt-get autoremove' to remove them.

(NOTE:  I used sudo apt-get autoremove to remove)

0 upgraded, 0 newly installed, 0 to remove and 6 not upgraded.
xxx@xxx:~$ sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv 643DC6BD56580CEB1AB4A9F63B22AB97AF1CDFA9
gpg: requesting key AF1CDFA9 from hkp server keyserver.ubuntu.com
gpg: key AF1CDFA9: "Launchpad PPA for Ubuntu-X" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
xxx@xxx:~$ sudo apt-get install bumblebee bumblebee-nvidia
Reading package lists... Done
Building dependency tree       
Reading state information... Done
**E: Couldn't find package bumblebee**
xxx@xxx:~$ sudo usermod -a -G bumblebee xxx
**usermod: group 'bumblebee' does not exist**

```

I'm a little afraid to reboot now, after "sudo apt-get autoremove" - have I removed anything I'll need for display after a reboot, since the bumblebee drivers didn't install?

EDIT:  May have figured it out...seems like I needed to do: 

sudo apt-get update
sudo apt-get install bumblebee bumblebee-nvidia

Seems to be installing something now.

---

### Post by Redflea on 2012-01-29
> **Redflea said:**
> 

EDIT:  May have figured it out...seems like I needed to do: 

sudo apt-get update

 -and then

sudo apt-get install bumblebee bumblebee-nvidia

Seems to be installing something now.

Install seemed to complete - all commands accepted.  Added:

```
For blacklisting to take effect, you may also have to update your initial ramdisk:

sudo update-initramfs -u
```

From [https://github.com/Bumblebee-Project/Bumblebee/wiki/Upgrading-on-Ubuntu](https://github.com/Bumblebee-Project/Bumblebee/wiki/Upgrading-on-Ubuntu)

Rebooted, and can't tell if the drivers are installed/activated.

jockey-text -l
```
kmod:nvidia_current - nvidia_current (Proprietary, Disabled, Not in use)
```

Hopefully I'm closer...  :)

Did find this:

lspci -k
```
01:00.0 VGA compatible controller: nVidia Corporation GT218 [GeForce 310M] (rev a2)
	[b]Kernel modules: nvidia-current, nouveau, nvidiafb01:00.0 VGA compatible controller: nVidia Corporation GT218 [GeForce 310M] (rev a2)
	Kernel modules: nvidia-current, nouveau, nvidiafb[/b]
```

And from hwinfo --gfxcard
```
Hardware Class: graphics card
  Model: "nVidia VGA compatible controller"
  Vendor: pci 0x10de "nVidia Corporation"
  
 Driver Info #0:
    Driver Status: nvidiafb is not active
    Driver Activation Cmd: "modprobe nvidiafb"
  [b]Driver Info #1:
    Driver Status: nouveau is active
    Driver Activation Cmd: "modprobe nouveau"[/b]
  Driver Info #2:
    Driver Status: nvidia_current is not active
    Driver Activation Cmd: "modprobe nvidia_current"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

```

So leave things as is?  Activate nvidiafb?

---

