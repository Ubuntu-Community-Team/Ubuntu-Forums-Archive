---
title: "Installed NVIDIA Drivers - Black screen with active mouse after login"
date: 2014-03-05
forum: Multimedia Software
---

### Post by AlwaysRemind on 2014-03-05
Hello everyone! I decided to completely ditch Windows 8 and let Ubuntu take the entire hard drive (Using UEFI+Secure Boot).

OS: Ubuntu 13.10
Computer: MSI GT70 0NC
CPU: [COLOR=#333333][FONT=Arial]Intel Core i7-3630QM[/FONT][/COLOR]
Graphics Card: [COLOR=#333333][FONT=Arial]NVIDIA GeForce GTX670MX
[/FONT][/COLOR]RAM: 12gig

Everything worked great! My webcam worked (great because I'm about to deploy) and everything seemed fine. I couldn't help but notice when I went to the system settings under Display it mentioned the Intel Graphics. I took it as if it didn't recognize my NVIDIA card.

I used the following command

```
sudo apt-get install nvidia-current
sudo reboot

```

After the reboot everything seemed fine. The login screen looked fine. After I logged in the screen, however, went black. The weird part is that I can still move the mouse and CTRL+ALT+T will open a Terminal. It's just I can't see any GUI.

After doing some research I saw a similar issue with a suggested resolution as the following:

```
sudo apt-get remove --purge nvidia*
```
then
```
sudo add-apt-repository pap:xorg-edgers/ppa
sudo apt-get update
sudo apt-get install nvidia-331
```
then it mentioned that bumblebee is the trouble maker and to finally run the following:
```
sudo apt-get --purge remove bumblebee sudo reboot
```

I was pretty hopeful but sadly this gave me the same exact outcome as the first. I can login and I'm just prompted with a black screen. I can move and see the mouse (the resolution seems right too based on the proportion of the mouse) and I can open the terminal via the shortcut. Just no GUI.

Any ideas on how I can fix this? Thank you so much you guys!

---

### Post by phidia on 2014-03-05
To restore your x server to a hopefully working default try one of the methods posted [here]("http://askubuntu.com/questions/21309/how-to-restore-xserver").

---

### Post by AlwaysRemind on 2014-03-05
Thank you very much. I checked out the thread you mentioned. There's a lot of talk about xorg.conf and I don't seem to have that file. I went ahead and ran:

```
sudo apt-get install --reinstall xserver-xorg
```

After this I noticed there still wasn't an xorg.conf file, so I ran this:

```
sudo nvidia-xconfig
```

When I rebooted, my resolution was extremely low at the login. After I logged in though I still have an all black screen with my mouse able to move around. I can still open the terminal as well. Any ideas? Thank you again so much for taking the time to help me.

---

### Post by Yellow Pasque on 2014-03-05
You need to completely remove any nvidia drivers you have installed and then follow this: [https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)

---

### Post by AlwaysRemind on 2014-03-05
Thank you I will try that right now. Just to make sure, to completely remove nvidia drivers I would need to use:

```
sudo apt-get remove --purge nvidia*
```

Right? Thank you again so much! I'll let you know if it worked!

---

### Post by Yellow Pasque on 2014-03-05
Yes, and make sure you remove the xorg.conf you created.

---

### Post by AlwaysRemind on 2014-03-05
I went ahead and ran this and rebooted afterwards following the guide:

```

sudo add-apt-repository ppa:bumblebee/stable
sudo apt-get update
sudo apt-get install bumblebee bumblebee-nvidia primus linux-headers-generic

```

The resolution is back to normal and I can see everything again. I'm not sure if this is the right way to determine if I'm using my graphics card or not, but when I go to Settings > Details it says for Graphics that I'm using Intel Ivybridge Mobile. Is there another way to determine if I'm actually using my 670MX? Thank you so much!

---

### Post by Yellow Pasque on 2014-03-05
If you want to run something on the nvidia GPU, you have to use optirun:
```
optirun glxinfo
optirun glxgears
optirun <insert game here>
```

---

### Post by AlwaysRemind on 2014-03-05
Thank you! Any idea on how that would work with Wine? I'm trying to run a game (WoW) and it only detected my Intel integrated card as well. Thank you again very much for taking the time to help me out!

---

### Post by Yellow Pasque on 2014-03-05
```
optirun wine somefile.exe
```

---

### Post by AlwaysRemind on 2014-03-05
Yesssss, you're amazing thank you!

---

### Post by AlwaysRemind on 2014-03-05
I do have a quick question, if  you don't mind. If the nvidia drivers installed correctly then how come  when I go to About this Computer it still says for graphics I'm using  Intel Ivybridge Mobile? I assumed it would display my graphics card  instead now?

---

### Post by Yellow Pasque on 2014-03-05
You **are** still using the Intel integrated graphics for anything you don't run with 'optirun' command to save battery and cut down on heat and fan noise (that's the whole point of the hybrid/Optimus thing). "About this Computer" just gets its info from glxinfo command and it's not programmed to check for presence of Optimus/Bumblebee. If you started the "About this Computer" from the terminal (don't know the command off the top of my head) and used optirun, it would show the nvidia driver info.

The difference in Windows is that the system picks what GPU to use based on load with the user having no idea what's going on underneath. For various technical/political reasons, Linux isn't there yet...

---

### Post by AlwaysRemind on 2014-03-05
Thank you so much! That makes a ton of sense. The only reason I was asking is because when WoW actually opens up with the optirun command, I only get around 30 fps. Is that normal for Ubuntu/wine even with a GPU? Thanks again!

---

