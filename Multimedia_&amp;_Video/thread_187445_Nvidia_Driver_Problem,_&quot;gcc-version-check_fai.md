---
title: "Nvidia Driver Problem, &quot;gcc-version-check failed&quot;"
date: 2006-06-03
forum: Multimedia &amp; Video
---

### Post by kevin.thome on 2006-06-03
Hello, I've been having a hard time installing nvidia drivers for my nvidia 7900 gt video card


I downloaded the .run off from nvidia's website and ran the command 

```
"sh NVIDIA-Linux-x86-1.0-8762-pkg1.run"
```

and this is what I got...


> 
gcc-version-check failed

Could not compile gcc-version-check.c. Please be sure you have your distribution's libc development package installed and that 'cc' is a valid c compiler name.

If you know what you are doing and want to ignore the gcc version check, select "no" to continue installation. Otherwise, select "yes" to abort installation, set the CC environment variable to the name of the compiler used to compile your kernel, and restart installation. Abort now?

-yes-  -no-


How do I go about getting this libc development package, and what's this " 'cc' is a valid compiler name" stuff about?

pardon my ignorance as I'm very new to ubuntu.


Thanks in advance,


-Kevin

---

### Post by Half-Left on 2006-06-03
Hi, 

Do ```
apt-get install build-essential
```

---

### Post by tseliot on 2006-06-03
Try my guide or, even better, my script:
[http://www.ubuntuforums.org/showthread.php?t=139264]("http://www.ubuntuforums.org/showthread.php?t=139264")

---

### Post by kevin.thome on 2006-06-03
I tried to use the script "envy_8762_32" but it just caused the kubuntu logo to appear (as it does when I boot up my computer) with the progress bar underneath stalled at zero progress.
So after waiting about 20 mins I decided to reboot and everything *seems* as it was before I ran the script.

---

### Post by kevin.thome on 2006-06-03
I also tried       

     *"apt-get install build-essential"*

then exited the gui and ran 

     *"sh NVIDIA-Linux-x86-1.0-8762-pkg1.run"*

and this is the error message I got:


[COLOR="red"] "Unable to find kernel source tree for the currently running kernel. Please be sure you have installed the kernel source files for your kernel and that they are properly configured. If you know where the correct kernel source files are installed, you may specify the kernel source path with the "--kernel-source-path" command line option"[/COLOR]

---

### Post by tseliot on 2006-06-04
[QUOTE=kevin.thome]I also tried       

     *"apt-get install build-essential"*

then exited the gui and ran 

     *"sh NVIDIA-Linux-x86-1.0-8762-pkg1.run"*

and this is the error message I got:


[COLOR="red"] "Unable to find kernel source tree for the currently running kernel. Please be sure you have installed the kernel source files for your kernel and that they are properly configured. If you know where the correct kernel source files are installed, you may specify the kernel source path with the "--kernel-source-path" command line option"[/COLOR][/QUOTE]
Please, follow Method 2 of my guide.

---

### Post by kevin.thome on 2006-06-04
I just tried method two, things seemed to work okay as i typed in the commands but then when I tried to get back into kde it was a nogo... the computer hangs at the kubuntu startup screen :(

---

### Post by michalv on 2006-07-19
Hi all, I have the same problems. I tried method 2 and the result was kubuntu start up screen and the computer is died. I have GF6600 graphic card. I will try the method 1 and I will see.

---

### Post by tseliot on 2006-07-19
> **kevin.thome said:**
> I just tried method two, things seemed to work okay as i typed in the commands but then when I tried to get back into kde it was a nogo... the computer hangs at the kubuntu startup screen :(

Try point 4 of the problems Section:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION)

---

### Post by tseliot on 2006-07-19
> **michalv said:**
> Hi all, I have the same problems. I tried method 2 and the result was kubuntu start up screen and the computer is died. I have GF6600 graphic card. I will try the method 1 and I will see.

Please don't mix the methods.

Try point 4 of the Problems Section:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION)

---

