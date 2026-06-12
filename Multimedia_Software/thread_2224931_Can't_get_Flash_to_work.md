---
title: "Can't get Flash to work"
date: 2014-05-19
forum: Multimedia Software
---

### Post by oygle on 2014-05-19
I'm trying to view a Flash video in Facebook. Have used [https://help.ubuntu.com/community/RestrictedFormats/Flash](https://help.ubuntu.com/community/RestrictedFormats/Flash) as a guide, but still can't view the video.

Even if I could convert the Flash video to MP4 or similar, that would be a better alternative.

---

### Post by Erik1984 on 2014-05-19
Do Flash videos on other sites (for example YouTube) work, and what browser are you using? Chrome ships the latest version of Flash.

---

### Post by mörgæs on 2014-05-19
And which processor? Please post the output from ```
sudo lshw -C cpu
``` in CODE tags.

---

### Post by oygle on 2014-05-19
> **Erik1984 said:**
> Do Flash videos on other sites (for example YouTube) work, and what browser are you using? Chrome ships the latest version of Flash.

Yes, I can view Flash videos in Youtube. I'm using Firefox; can't find the 'About' to check version, but in .../archives, the firefox .DEB looks like 29.0


> **mörgæs said:**
> And which processor? Please post the output from ```
sudo lshw -C cpu
``` in CODE tags.

```
:~$ **sudo lshw -C cpu**
[sudo] password for ******: 
  *-cpu                   
       description: CPU
       product: Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz
       vendor: Intel Corp.
       physical id: 4
       bus info: cpu@0
       version: Intel(R) Core(TM)2 Quad CPU Q6600 @ 2.40GHz
       serial: To Be Filled By O.E.M.
       slot: LGA775
       size: 1603MHz
       capacity: 3800MHz
       width: 64 bits
       clock: 266MHz
       capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx constant_tsc arch_perfmon pebs bts rep_good nopl aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm lahf_lm dtherm tpr_shadow vnmi flexpriority cpufreq
       configuration: cores=4 enabledcores=4 threads=4
:~$ 

```

Hmm, I just tried the Flash video in Facebook again, and I can see it okay now ?? Yesterday I did try adding and deleting packages in Muon, that were names "Flash". Now the only one there is 'flashplugin-installer'.   :confused:

Now that it seems it can work in Facebook, is there a method to convert the Flash to MP4, so that I can play it offline ?

Oygle

---

### Post by slooksterpsv on 2014-05-19
You can download a plugin for firefox (or chrome) to download the flash files as FLV, then use an app like WinFF to convert from FLV to MP4.

---

### Post by monkeybrain20122 on 2014-05-19
To check if you actually have flash installed, in Firefox go to Tools > Addons > Plugins and see if there is an entry for flash and that it is activated (best option: ask to activate) Youtube works without flash as most videos now play in html5.

It should work if you install ubuntu-restricted-extras if it is just a facebook flash video (unless you are playing flash games, in that case you may need chrome). It always works for me. But if for some reasons it is not working for you install greasemonkey addon for Firefox, get gecko-mediaplayer from repo, and install the greasemonkey script viewtube, which also works on facebook videos [http://isebaro.com/viewtube/?ln=en](http://isebaro.com/viewtube/?ln=en)
> 
Now that it seems it can work in Facebook, is there a method to convert the Flash to MP4, so that I can play it offline ?

Viewtube has a download option (get) , as does gecko-mediaplayer.

---

### Post by oygle on 2014-05-19
> **slooksterpsv said:**
> You can download a plugin for firefox (or chrome) to download the flash files as FLV, then use an app like WinFF to convert from FLV to MP4.

I have tried 2 plugins now, "Flash Video Downloader - Full HD Download 5.9.1" and "Flash and Video Downoload 1.55" , and they both downloaded the Flash as MP4. Quality is very poor though.

> **monkeybrain20122 said:**
> To check if you actually have flash installed, in Firefox go to Tools > Addons > Plugins and see if there is an entry for flash and that it is activated (best option: ask to activate) Youtube works without flash as most videos now play in html5.

At the moment I have "Flash Video Downloader - Full HD Download 5.9.1", but quality is poor (The Flash video on Facebook was much better).

> **monkeybrain20122 said:**
> 
It should work if you install ubuntu-restricted-extras if it is just a facebook flash video (unless you are playing flash games, in that case you may need chrome). It always works for me. But if for some reasons it is not working for you install greasemonkey addon for Firefox, get gecko-mediaplayer from repo, and install the greasemonkey script viewtube, which also works on facebook videos [http://isebaro.com/viewtube/?ln=en](http://isebaro.com/viewtube/?ln=en)

Viewtube has a download option (get) , as does gecko-mediaplayer.

Okay thanks, I will try that then. Seems it is kubuntu-restricted-extras fr Kubuntu, and I haven't used anything from the repo that is multiverse beforehand. I did try finding out at [http://www.ubuntu.com/about/about-ubuntu/licensing](http://www.ubuntu.com/about/about-ubuntu/licensing) , but nothing helpful about multverse.

---

### Post by monkeybrain20122 on 2014-05-19
> **oygle said:**
> 


At the moment I have "Flash Video Downloader - Full HD Download 5.9.1", but quality is poor (The Flash video on Facebook was much better).

.

You are in the addon section, go to plugins. I think you probably haven't had flash installed at all.

> Okay thanks, I will try that then. Seems it is kubuntu-restricted-extras  fr Kubuntu, and I haven't used anything from the repo that is  multiverse beforehand 

Doesn't matter which repo it is from, they are all in the same pool and you install software the same way with muon or apt-get.

---

### Post by oygle on 2014-05-19
> **monkeybrain20122 said:**
> You are in the addon section, go to plugins. I think you probably haven't had flash installed at all.

Yes, you are correct. The plugins say "Shockwave Flash 11.2.202.359"

---

### Post by slooksterpsv on 2014-05-21
Was it better because it was scaled down on Fb and not after MP4 conversion? Or is the file really just bad?

---

### Post by oygle on 2014-05-21
> **slooksterpsv said:**
> Was it better because it was scaled down on Fb and not after MP4 conversion? Or is the file really just bad?

Yes, it looks better on FB, probably because it is scaled down (not viewed in full screen). I am now using the "HD" button when playing in FB, and then using the Firefox add-on "Flash Video Downloader - Full HD Download 5.9.1" to download, the quality is quite acceptable , even in full screen.

Have removed the package 'kubuntu-restricted-extras' , as all is working okay without it. So, in suumary it is working okay with

*  Shockwave Flash 11.2.202.359 plugin
*  Flash Video Downloader - Full HD Download 5.9.1  -  add-on

Thanks everyone for your help. Will mark this as solved now.   :)

---

### Post by oygle on 2014-10-03
Realised this was "solved", so have put the question at [http://ubuntuforums.org/showthread.php?t=2246885](http://ubuntuforums.org/showthread.php?t=2246885)

---

