---
title: "Will an Acer Aspire 7 laptop run Linux Mint (or any other Debian based distro)?"
date: 2019-06-20
forum: MINT
---

### Post by kernel-dressing1 on 2019-06-20
Hello, I'm very new to the world of Linux. I've had a desktop that ran Windows 7 forever and I was really happy with that operating system, but then the hdd it was running on failed. so I got a new drive and windows 10. I really don't like Windows 10 and I was wondering if my laptop would be able to run Linux Mint since I hear it is sort of similar to Windows 7 in its aesthetics. It's this model of laptop right here [https://www.amazon.com/Acer-Display-i7-8750H-Fingerprint-A715-72G-71CT/dp/B07CZC81F6](https://www.amazon.com/Acer-Display-i7-8750H-Fingerprint-A715-72G-71CT/dp/B07CZC81F6)
I'm mainly concerned that the 1050 ti graphics card and fingerprint reader won't run well on Linux since I heard that there is limited support for that sort of hardware.

I mainly plan on using that laptop to do some programming with android studio/notepad++/Clion/Microsoft Visual Studio Code, and photo editing/video editing and 3d rendering with blender/unity. I think I can get by with that laptop not having microsoft office because I have a desktop at home with that installed. Gaming on that laptop is sort of a secondary thing.

Do you think Linux Mint would run those sorts of programs and still allow me to use things like the graphics card and fingerprint scanner? Or would it be better to just stick with Windows 10?
Thanks for any help that anyone can offer me.

---

### Post by TheFu on 2019-06-20
Try it out. Nothing to loose.  The GUI should work. nvidia drivers are available - just don't get them from nvidia. Use the tested versions from Mint/Ubuntu using the built-in driver manager.

If this is your first Linux/Unix experience, there is a steep learning curve.  Windows knowledge doesn't really transfer to any other OS.  Unix systems are extremely different from Windows.

As for the fingerprint reader - fingerprints are terrible security. If you care about security, use a U2F key-fob.  Pretty much all fingerprint readers are anti-security. They are a card trick, nothing more. Definitely NOT secure.

I'd never tell anyone to stick with Win10. NEVER.  I've read the EULA and would never agree to that.

A quick overview of Linux compared to Windows will help you decide: [https://www.dedoimedo.com/computers/ultimate-linux-guide-for-windows-users.html](https://www.dedoimedo.com/computers/ultimate-linux-guide-for-windows-users.html) from 2014, but still relevant.

Android programming requires a fairly beefy system, thanks to java, which is always a dog on all computers.  A Core i7 with 16G of RAM would be my minimal Android development system.

notepad++ - linux has 50 better editors.  
I haven't touched any Microsoft programming tools since the 1990s. Just not used much on Linux systems.
Video editing tools on Linux are very powerful for content creators. I'm interested in content editing/cutting and for that, Linux tools aren't the easiest to use. I still use Windows for that.

"Unity" means something specific in Ubuntu, probably not what you think coming from Windows.  

You need to understand that Linux is a different OS than Windows and the APIs are completely different. Programs created for Windows don't run on Linux usually.  Some tiny subset, usually simple programs, might work with WINE, but most will not.

If you don't need a laptop for portability, you can build a faster desktop for about 50% less money using a Ryzen5 CPU.  If the system is available over the internet via an ssh connection, then you can do all the programming remote on the faster system from almost any client machine.  People program using iPads and Android tablets in this way, though I prefer to use $200 laptops to access my faster desktop(s) for programming when that is needed.  For non-Java programming, a $200 laptop can usually suffice.  I've done webapp development on chromebooks for years.

---

### Post by coffeecat on 2019-06-20
*Moved to Mint sub-forum.*

---

### Post by oldfred on 2019-06-20
Do not know what differences may be with Mint.
But all Acer have several requirements for Linux.
You need to update UEFI, and if SSD update firmware.
You will need to set "trust" on the UEFI boot entry from within UEFI after install.
If nVidia you will need nomodeset to install & first boot or until you install nVidia driver from repository. Do not know if Mint uses same repository or not.

General UEFI install steps in link in my signature below.

If RAID 0, do not change drive settings, otherwise drives need to be AHCI, not RAID nor Intel RST.

       How to install Ubuntu for dual-boot with Windows 8 on Acer Aspire V5-551G. Post #3 Supervisory password required
[URL="http://ubuntuforums.org/showthread.php?t=2176273"]http://ubuntuforums.org/showthread.php?t=2176273
      [/URL]
 Acer Aspire ES1-512-C39M Details on supervisor password and settings to enable trust on ubuntu entries Also R14 model same fix
[http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044](http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044)
[http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot](http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot)
[http://acer.custhelp.com/app/answers/detail/a_id/29349/](http://acer.custhelp.com/app/answers/detail/a_id/29349/)
[http://ubuntuforums.org/showthread.php?t=2290594](http://ubuntuforums.org/showthread.php?t=2290594) 
    
These essentially are all the same, slight differences which may help in details.
       Acer Trust Settings - details, some now report that then secure boot has to be on to set trust:
[https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742) & 
[https://ubuntuforums.org/showthread.php?t=2297947](https://ubuntuforums.org/showthread.php?t=2297947) & 
[https://ubuntuforums.org/showthread.php?t=2358003](https://ubuntuforums.org/showthread.php?t=2358003) 
    [URL="http://ubuntuforums.org/showthread.php?t=2176273"]
      [/URL] At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters) & 
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132) 
    [ ]("http://ubuntuforums.org/showthread.php?t=2176273")

---

