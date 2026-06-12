---
title: "Installing Latest NVidia Proprietary Drivers on 64 bit Lucid 10.04"
date: 2011-01-12
forum: Multimedia Software
---

### Post by shreepads on 2011-01-12
Hi folks

Thought I'd put this together based on what I just did as it's hard to find a place where you get complete info in one place for this topic.

Not taking any credit as it's just piecing together stuff found on the net.

Of course this is for my specific hardware and system so YMMV:
- Palit Sonic GT 240 card
- Lucid 10.04.1 64-bit
- Intel DG33FB board and E7200 CPU
- LG monitor L194WT at 1440x900 res

Reason for choosing the latest NVidia drivers instead of the ones available from the System > Administration > Hardware Drivers option is that the latest ones contain specific fixes for my card, that are not available in the others.

_**Prerequisites:**_

All of the following is based on a freshly installed 64-bit Lucid 10.04.1 system. Some actions may need modification if you have already been tinkering with Nvidia drivers.

1. Backup your /etc/X11/xorg.conf file if any. The default clean install of 64-bit Lucid 10.04.1 doesn't create this file so unless you have generated and modified the xorg.conf file for your specific needs, skip this.

2. Install the following packages

```
sudo apt-get install build-essential linux-headers-`uname -r`
```

If this doesn't work, run 

```
uname -r
```

and paste the output of that in the command above so you get, say

```
sudo apt-get install build-essential linux-headers-2.6.32-27-generic
```

3. Remove the following packages using Synaptic's 'Completely Remove' option
- nvidia-173-modaliases
- nvidia-96-modaliases
- nvidia-current-modaliases
- nvidia-common

4. Create a new text file *disable-nouveau.conf* in the directory */etc/modprobe.d/* with the following contents

```
blacklist nouveau
options nouveau modeset=0


```

5. Download the latest NVidia drivers applicable to your card from here:
     [http://www.nvidia.com/Download/index.aspx](http://www.nvidia.com/Download/index.aspx)
   
6. Save the downloaded file (e.g. NVIDIA-Linux-x86_64-260.19.29.run in my case) to an easily accessible location like your home folder. Make this file executable by running, say

```
sudo chmod +x NVIDIA-Linux-x86_64-260.19.29.run
```

7. Check that the driver was correctly downloaded.

```
sh NVIDIA-Linux-x86_64-260.19.29.run --check
```

8. Run Update Manager, Check for updates and Apply any found


**_Installation:_**

1. Restart and choose the recovery option from the Grub options list.

2. Choose the Root Shell option in the list of options presented subsequently.

3. At the root shell run the following
```

telinit 3
```

If you skip this, the driver installer will inform you of the need to do this.

4. This will present you with a login prompt. Login with your admin username and password.

5. Navigate to the folder where the driver installer is present and run it, like

```
sudo sh NVIDIA-Linux-x86_64-260.19.29.run
```

6. Accept the license text.

7. Say Yes to installing the 32-bit Open GL drivers.

8. I think you need to say Yes/ Accept once more time to initiate the driver installation.

9. Once the driver is installed it will ask you whether it should configure xorg.conf for you, say Yes. This will create the xorg.conf file if not present in your system and modify an existing one if present.

10. Back at the prompt, shutdown the system

```
sudo init 0
```

11. Restart and use the normal startup option in the Grub options list, if all goes well you should see your beautiful desktop.

---

### Post by jdsmofo on 2011-03-21
Yeah, I did all of this, and it went exactly as described.  Still Xorg is using 30-50% of my CPU making all work unbearably slow.  This is a Dell XPS M1330 notebook.  Typing

lspci | grep VGA

returns

01:00.0 VGA compatible controller: nVidia Corporation G86 [GeForce 8400M GS] (rev a1)

I go to NVIDIA's site to download what they say is the appropriate driver.  My OS is Kubuntu 10.04, 64bit.

I have tried every recommendation there is on the intertubes, and nothing keeps Xorg from consuming way to much CPU time.

---

