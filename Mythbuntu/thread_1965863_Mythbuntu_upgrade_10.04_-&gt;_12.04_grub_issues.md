---
title: "Mythbuntu upgrade 10.04 -&gt; 12.04 grub issues"
date: 2012-04-26
forum: Mythbuntu
---

### Post by TrueBlueBlooded on 2012-04-26
> 
**Known issues**

Upgrading from 10.04 -> 12.04 will result in a broken system (grub isn't installed properly)
 This appears in the Mythbuntu 12.04 release notes but not the Ubuntu 12.04 release notes.  I'm glad I saw it before attempting to upgrade my Mythbuntu 10.04 system.

Is there a fix/workaround?

---

### Post by tgm4883 on 2012-04-26
> **TrueBlueBlooded said:**
> This appears in the Mythbuntu 12.04 release notes but not the Ubuntu 12.04 release notes.  I'm glad I saw it before attempting to upgrade my Mythbuntu 10.04 system.

Is there a fix/workaround?

It doesn't happened for everyone, but if it does happen you will need a bootable 12.04 ISO to install grub with.

---

### Post by grg3 on 2012-04-27
I haven't had the need to upgrade a 10.04 Mythbuntu install, but I have seen grub issues with 10.04 and higher before.

I am sure that there are posts about this subject. The procedure that is easiest for me is to have an alternate Ubuntu CD handy. I know there may be better ways, but I am lazy and I like quick and easy.

Sometimes upgrades from 10.04 install the new grub and sometimes they don't. I had to remove grub legacy and install grub-pc on my uncle's desktop when I upgraded this morning.

Anyway, my grub fix with the alternate cd is this:

Boot the alt-cd and select rescue broken system and take all the defaults until you get to select root.

Pick your root filesystem (usually sda1)

Either ... select reinstall grub from menu or

execute a shell in /dev/sda1 (your root) and at the prompt type

update-grub <enter>
grub-install /dev/sda <enter>
exit

reboot the system. If grub-pc is installed this should take care of your grub.

---

### Post by grg3 on 2012-04-27
I just did the upgrade to 12.04 on my 11.10 backend and had to reinstall grub. Oddly, my frontend upgraded with no problem.

---

### Post by anonymousdog on 2012-05-02
Is there any predictability on this issue?...any pre-existing conditions that seem to lead to the problem during upgrade?

---

### Post by wb4alm on 2012-09-03
> **anonymousdog said:**
> Is there any predictability on this issue?...any pre-existing conditions that seem to lead to the problem during upgrade?

My system started out as 08.04 LTS, upgraded to 10.04 LTS, upgraded to 12.04.1 LTS.

It failed to boot, and what I found was that the command 
"initrd /boot/initrd.img-3.2.0-29-generic" statement was not present in the startup script....   

If I manually add this commend using the "E" option when selecting the appropiate image then I can boot to the upgraded system. 

my reading seems to indicate that this will occur when the newer grub and the older grub are both "installed" in the same system...

While I am experienced in computers, I am not an expert in Linux. So, here is a question...

1. how do I find out if both grubs are present in my system, and what do I do to fix the issue?
    [COLOR="Red"]identify the version:[/COLOR]
        [COLOR="Blue"]sudo grub-install -v[/COLOR]  
    [COLOR="Red"]reinstall (and convert) to grub2:[/COLOR]  
        [COLOR="Blue"]sudo apt-get install grub-pc --reinstall
[/COLOR]
2. Is there a way to update the grub startup script so that I do not have to manually enter the "initrd" statement each time I boot?
    [COLOR="Red"]When grub2 is the -only- version installed then[/COLOR]
        [COLOR="Blue"]sudo update-grub[/COLOR]
    [COLOR="Red"]will build a valid grub startup script.[/COLOR]

---

### Post by dibuntux on 2012-11-16
Just upgraded from 10.04.1 lts amd64 to 12.04 lts: no problem with grub. Everything was smooth execpt:

1) remote was not working - just selected a different one in mythcontrol center and then selected again the right one and it was working again.

2) on livetv and video I got "fail to initialize video out". The restricted driver was not set to Nvidia - just selected the recomended driver: dowloaded, installed and restart system - OK

3) Set audio to DTS on to activate DTS in Audio setup

That's it! Fantastic work Mythbuntu team!:):)

---

### Post by GaryP2 on 2012-11-16
> **dibuntux said:**
> 2) on livetv and video I got "fail to initialize video out". The restricted driver was not set to Nvidia - just selected the recomended driver: dowloaded, installed and restart system - OK

Can you elaborate on this? Did you not choose to use the NVIDIA driver when you did the initial ISO install and had to go back and install it after the fact, or is there another setting you found where you have to choose NVIDIA?
 
Also, is this 12.04/Myth .25 or have you upgraded MythTV to .26 since installing the Mythbuntu ISO?
 
I’m just trying to understand if there I a setting I should look out for when I upgrade to .26. I choose NVIDIA during the initial install and my .25-fixes BE/FE FE Live TV works great. Thanks much.

---

