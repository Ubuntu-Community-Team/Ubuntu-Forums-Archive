---
title: "Problem running upscaryl"
date: 2023-09-22
forum: Multimedia Software
---

### Post by satimis on 2023-09-22
Problem running upscaryl

**[COLOR="#FF0000"]Ubuntu 22.04 VM of Virtual Box[/COLOR]**

I have installed**[COLOR="#FF0000"][COLOR="#FF0000"] Upscayl [/COLOR][/COLOR]**running snap.  It can be started but unable to restore old photos

Warning - please refer to photo attached

Please help.  Thanks

$ cat /proc/cpuinfo  | grep 'name'| uniq```

model name      : AMD Ryzen 5 3400G with Radeon Vega Graphics
```

---

### Post by Dennis N on 2023-09-23
There are two similar programs **Upscayl** and **Upscaler**. I've had good results with **Upscaler** so I haven't bothered with **Upscayl**. Both use the same AI algorithm. Results will vary with the quality of the source. You can get either of these as a Flatpak. I don't care for Snaps if there is an alternative.

---

### Post by satimis on 2023-09-23
> **Dennis N said:**
> There are two similar programs **Upscayl** and **Upscaler**. I've had good results with **Upscaler** so I haven't bothered with **Upscayl**. Both use the same AI algorithm. Results will vary with the quality of the source. You can get either of these as a Flatpak. I don't care for Snaps if there is an alternative.
Hi,

Flatpak is running on Ubuntu 22.04 desktop

$ flatpak install Upscaler```

Looking for matches&#8230;
Similar refs found for &#8216;Upscaler&#8217; in remote &#8216;flathub&#8217; (system):

   1) app/page.codeberg.JakobDev.jdPixelUpscaler/x86_64/stable
   2) app/io.gitlab.theevilskeleton.Upscaler/x86_64/stable

Which do you want to use (0 to abort)? [0-2]: 
```

Which package shall I install,  1) or 2) ?
 
Thanks

---

### Post by Dennis N on 2023-09-23
Upscaler is number 2: (io.gitlab.theevilskeleton.Upscaler)

Note: I haven't tried Upscayl, so can't say one is better than the other! Upscaler did what I wanted, so that was that.

---

### Post by Dennis N on 2023-09-23
There was a story on the OMG Ubuntu! website about Upscaler. You might want to read that.
[https://www.omgubuntu.co.uk/2022/11/upscaler-open-source-ai-image-upscale-app-for-linux](https://www.omgubuntu.co.uk/2022/11/upscaler-open-source-ai-image-upscale-app-for-linux)

---

### Post by satimis on 2023-09-23
> **Dennis N said:**
> Upscaler is number 2: (io.gitlab.theevilskeleton.Upscaler)

Note: I haven't tried Upscayl, so can't say one is better than the other! Upscaler did what I wanted, so that was that.
Thanks.

Now I have Upscaler installed.  I can start it and import image.  But I have no way to use it. Please see attached image

Where can I find its tutorial?  Thanks

---

### Post by Dennis N on 2023-09-23
You are partly done. To complete the job:

Choose a save Location, click "save" in the file chooser, then click on the "Upscale" button.
Wait until it finishes.
When it says "image upscaled" click "open" and choose an image viewer to view the result. See screenshot of final window **&#8595;**

The result is always 4x the original. That's a fixed setting of the AI algorithm.

---

### Post by satimis on 2023-09-23
> **Dennis N said:**
> You are partly done. To complete the job:

Choose a save Location, click "save" in the file chooser, then click on the "Upscale" button.
Wait until it finishes.
When it says "image upscaled" click "open" and choose an image viewer to view the result. See screenshot of final window **&#8595;**

The result is always 4x the original. That's a fixed setting of the AI algorithm.
Always error

Error while processing```


Algorithm failed.
Result code: -6
Output: [0 llvmpipe (LLVM 15.0.7, 256 bits)]  queueC=0[1]  queueG=0[1]  queueT=0[1]
[0 llvmpipe (LLVM 15.0.7, 256 bits)]  bugsbn1=0  bugbilz=88  bugcopc=0  bugihfa=0
[0 llvmpipe (LLVM 15.0.7, 256 bits)]  fp16-p/s/a=1/1/0  int8-p/s/a=1/1/1
[0 llvmpipe (LLVM 15.0.7, 256 bits)]  subgroup=8  basic=1  vote=1  ballot=1  shuffle=1
LLVM ERROR: Cannot select: 0x7f5c601e82b8: i16,ch = X86ISD::FILD<(load (s16) from %stack.10)> 0x7f5c601e74e8, FrameIndex:i64<10>
  0x7f5c601e7ca0: i64 = FrameIndex<10>
In function: cs_co_variant

```

---

### Post by Dennis N on 2023-09-23
I don't know what your error message means. Did you try with other images to see if it's a general problem?

---

### Post by #&amp;thj^% on 2023-09-23
If it matters I dumped the flatpak, and installed the.deb: [https://github.com/upscayl/upscayl/releases](https://github.com/upscayl/upscayl/releases)
Same as satimis for my flatpak use, wasn't the way to go.
```
 apt policy upscayl
upscayl:
  Installed: 2.8.6
  Candidate: 2.8.6
  Version table:
 *** 2.8.6 100
        100 /var/lib/dpkg/status

```
I use it for some of my nicer Wallpapers and Family Photos, I don't set save file as default i put it in another folder.

---

### Post by satimis on 2023-09-24
> **1fallen said:**
> If it matters I dumped the flatpak, and installed the.deb: [https://github.com/upscayl/upscayl/releases](https://github.com/upscayl/upscayl/releases)
Same as satimis for my flatpak use, wasn't the way to go.
```
 apt policy upscayl
upscayl:
  Installed: 2.8.6
  Candidate: 2.8.6
  Version table:
 *** 2.8.6 100
        100 /var/lib/dpkg/status

```
I use it for some of my nicer Wallpapers and Family Photos, I don't set save file as default i put it in another folder.
Hi 1fallen,

I'll try again.  Previsouly I tested Upscayl on Ubuntu 22.04 VM.  Would it matter?  If NO I will clone another Ubuntu 22.04 VM and install the package from your link.

Please advise.  Thanks

Regards

---

### Post by #&amp;thj^% on 2023-09-24
> **satimis said:**
> 
 Previsouly I tested Upscayl on Ubuntu 22.04 VM.  Would it matter?  If NO I will clone another Ubuntu 22.04 VM and install the package from your link.

Please advise.  Thanks

Regards

I think that it would matter.
When it comes to re-encode or up scaling I want the full power of my current running OS's hardware for best results.
Again the flatpak version had far to many errors for my taste, the .deb just works. :)

---

### Post by satimis on 2023-09-24
> **1fallen said:**
> I think that it would matter.
When it comes to re-encode or up scaling I want the full power of my current running OS's hardware for best results.
Again the flatpak version had far to many errors for my taste, the .deb just works. :)
Hi 1fallen,

OK.

I'll find an old SSD to install Ubuntu 22.04 and Upscaryl, running it on bare-metal.  I'll come back to report my testing.

Regards

---

### Post by Dennis N on 2023-09-24
Hey,

I just installed **Upscayl** to see how it differs from **Upscaler**. After a couple of tests, I found it very good. I like the comparison slider view after the upscaling. Neat. Not on Upscaler. Also the batch processing option not in Upscaler. I'm probably using this from now on.

Comments:
I have been using Upscale because I saw it in the OMG Ubuntu article last year. It has been working well for me.
I installed Upscayl from the Flatpak and had no problems in the tests, so I will stick with that.
I agree a VM install might not work well.
On older computers these programs may not work at all. I have one case.

---

### Post by #&amp;thj^% on 2023-09-24
> **Dennis N said:**
> Hey,

I just installed **Upscayl** to see how it differs from **Upscaler**. After a couple of tests, I found it very good. I like the comparison slider view after the upscaling. Neat. Not on Upscaler. Also the batch processing option not in Upscaler. I'm probably using this from now on.

Comments:
I have been using Upscale because I saw it in the OMG Ubuntu article last year. It has been working well for me.
I installed Upscayl from the Flatpak and had no problems in the tests, so I will stick with that.
I agree a VM install might not work well.
On older computers these programs may not work at all. I have one case.

Thanks Dennis N it's good to see differences from other users as well, until something better comes along it's my go to for my very small needs.

---

### Post by Dennis N on 2023-09-24
**@Satimis;**

Reading the Upscayl FAQ on their website, this might explain why it fails for you:

> Do I need a GPU for this to work?

Yes, unfortunately. Upscayl uses Real-ESRGAN-ncnn-vulkan binaries to upscale images. NCNN Vulkan requires a Vulkan-compatible GPU. Upscayl won't work with most iGPUs or CPUs. But hey, no harm in trying ;) 

It does work for me with both Intel gen 8 and 12 integrated graphics. 

Note iGPU = integrated graphics with the processor.

---

### Post by satimis on 2023-09-24
> **Dennis N said:**
> **@Satimis;**

Reading the Upscayl FAQ on their website, this might explain why it fails for you:



It does work for me with both Intel gen 8 and 12 integrated graphics. 

Note iGPU = integrated graphics with the processor.
Whether I need a PC with graphic not coming from CPU?

I can make another test on my spare PC, graphic not coming from the AMD CPU.  Can I test upscaryl on VM of Orale Virtual Box?  Thanks

---

### Post by Dennis N on 2023-09-24
> **satimis said:**
> Whether I need a PC with graphic not coming from CPU? I can make another test on my spare PC, graphic not coming from the AMD CPU.  Can I test upscaryl on VM of Orale Virtual Box?  Thanks

It's not necessary to have separate graphics. I don't, and the programs (both of them) work well. It just may take longer to process an image. If your machine is relatively new, the CPU with integrated graphics should do the job if Vulkan-compatible. Specs on my Intel gen 8 and 12 processors indicates these are.  

1Fallen commented that a virtual machine is probably not the best place to run of these. I agree with that comment. But, you can try if you have a powerful machine - it may work fine.

---

### Post by #&amp;thj^% on 2023-09-24
> **satimis said:**
> Whether I need a PC with graphic not coming from CPU?

I can make another test on my spare PC, graphic not coming from the AMD CPU.  Can I test upscaryl on VM of Orale Virtual Box?  Thanks

I agree with Dennis N I have both amdgpu and nvidia both just work.
Outside of course I had failures with the flatpak on this same machine, but the .deb just works all the time.
That said It could be hardware difference as well, you and I are both AMD Ryzen and Dennis N is Intel  iGPU = integrated graphics with the processor.
I think your going to have better outcomes on a real OS non VM's

---

### Post by satimis on 2023-09-27
Hi all,

Now I have Upscayl installed on an old SATA SSD running on Terminal;
$ flatpak install Upscayl

OS - Ubuntu 20.04 desktop
Upscayl 2.8.1

I can start Upscayl.  Please advise where can I find document running it to restore old photos?  Thanks

Regards

---

### Post by Dennis N on 2023-09-27
> **satimis said:**
> I can start Upscayl.  Please advise where can I find document running it to restore old photos?  Thanks

Regards

Well, you may be overly optimistic about Upscayl or Upscaler. They can't fix everything you might want. You get an image four times the size of the original with the goal of not introducing pixelation or blurring. The results may even appear sharper than the original. You have to see for yourself what these programs can accomplish. 

These two programs don't include options to modify coloration, saturation, contrast, brightness or other qualities of the image (if they do, they're not apparent). You can find commercial programs that can do amazing adjustments using AI, but what I see available is only for Windows or Mac at this time!

---

### Post by satimis on 2023-09-27
> **Dennis N said:**
> Well, you may be overly optimistic about Upscayl or Upscaler. They can't fix everything you might want. You get an image four times the size of the original with the goal of not introducing pixelation or blurring. The results may even appear sharper than the original. You have to see for yourself what these programs can accomplish. 

These two programs don't include options to modify coloration, saturation, contrast, brightness or other qualities of the image (if they do, they're not apparent). You can find commercial programs that can do amazing adjustments using AI, but what I see available is only for Windows or Mac at this time!
Hi,

Yes, Upscayl only upgrades the resolution of photo, nothing else.  On step-4 the resolution of the photo to be upgraded is pre-set by the program.  I can't make any change.  It takes long time to complete.

To upgrade resolution of photos I can run ffmpeg on Terminal.

I think I need AI.  Is AI FREE?  I can test it on WINE simulator.  Besides I have Windows running here, bare-metal as well as VM of VirtualBox

GIMP can do the job but it takes long time to edit one photo

Regards

---

### Post by Dennis N on 2023-09-27
Google search for AI photo editors. There are YouTube videos that show the features and what is possible with AI. For example, I looked a few days ago at at a video on one called Luminar Neo. Impressive. Windows and Mac only.

---

### Post by satimis on 2023-09-27
> **Dennis N said:**
> Google search for AI photo editors. There are YouTube videos that show the features and what is possible with AI. For example, I looked a few days ago at at a video on one called Luminar Neo. Impressive. Windows and Mac only.
There are many AI photo editors for Windows, all paid

I found one for Linux
**[COLOR="#FF0000"]Imaginer – Your AI Image creator on Linux Desktop[/COLOR]**
[https://www.linuxfordevices.com/tutorials/linux/imaginer-ai-image-creator](https://www.linuxfordevices.com/tutorials/linux/imaginer-ai-image-creator)

I'll test it on Ubuntu 22.04 VM

---

### Post by Dennis N on 2023-09-27
> **satimis said:**
> There are many AI photo editors for Windows, all paid

I found one for Linux
**[COLOR="#FF0000"]Imaginer – Your AI Image creator on Linux Desktop[/COLOR]**
[https://www.linuxfordevices.com/tutorials/linux/imaginer-ai-image-creator](https://www.linuxfordevices.com/tutorials/linux/imaginer-ai-image-creator)

I'll test it on Ubuntu 22.04 VM

Do you think this is an editor? It's described as an image creator - a program that works from user suggestions to create a result. After reading the page, I'm not sure you could load an existing image to edit. Let me know what you find after your test.

---

### Post by satimis on 2023-09-28
> **Dennis N said:**
> Do you think this is an editor? It's described as an image creator - a program that works from user suggestions to create a result. After reading the page, I'm not sure you could load an existing image to edit. Let me know what you find after your test.
Yes, you're right.  I have tested it on Ubuntu 22.04 desktop. It is not AI photo editor

**topaz is for Linux and Windows but is not FREE**

**[COLOR="#FF0000"]TOPAZ[/COLOR]**
[https://www.topaz.sh/docs/getting-started#:~:text=topaz%20is%20available%20on%20Linux,tarballs%20in%20the%20release%20page.&text=Download%20the%20topaz_windows_x86_64.,page%20and%20execute%20the%20MSI](https://www.topaz.sh/docs/getting-started#:~:text=topaz%20is%20available%20on%20Linux,tarballs%20in%20the%20release%20page.&text=Download%20the%20topaz_windows_x86_64.,page%20and%20execute%20the%20MSI).

I found follow:
**[COLOR="#FF0000"]The Best Free AI Photo Editors[/COLOR]**
[https://www.alphr.com/best-free-ai-photo-editors/](https://www.alphr.com/best-free-ai-photo-editors/)

**[COLOR="#FF0000"]3. Generated.photos[/COLOR]**
**Pros**
Free plan
Lots of images to work with
Tools help you achieve unique results

**Cons**
You need a license to use the images commercially

**[COLOR="#FF0000"]6. Hotpot Tools[/COLOR]**
**Pros**
Images processed quickly
Many free features
**[COLOR="#FF0000"]You can work with old photos[/COLOR]**

**Cons**
Photos are processed slower in the free version

**I'll test "6. Hotpot Tools" on Ubuntu 22.04 VM**

What will be your suggestion?

Regards

---

### Post by Dennis N on 2023-09-28
Probably #6 because of the comment that you can work with old photos. That was your objective, right?
Please report back how it worked out.

---

### Post by satimis on 2023-09-28
> **Dennis N said:**
> Probably #6 because of the comment that you can work with old photos. That was your objective, right?
Please report back how it worked out.
On further checking their website it was discovered that they only offer free online service.  The tools are not for download.  However the Free tools are limited.  You have to pay for additional tools

Regards

---

### Post by Dennis N on 2023-09-28
> **satimis said:**
> On further checking their website it was discovered that they only offer free online service.  The tools are not for download.  However the Free tools are limited.  You have to pay for additional tools
Regards

I noticed that. You may not find a downloadable option for these more powerful tools. They also want to monetize their product, so they need to charge for some things. I get that. ChatGPT from OpenAI is online. A graphics generating counterpart DALL-E2 is also. I intend to try these out before too long.  Millions use it, including our students!

---

### Post by satimis on 2023-09-28
> **Dennis N said:**
> I noticed that. You may not find a downloadable option for these more powerful tools. They also want to monetize their product, so they need to charge for some things. I get that. ChatGPT from OpenAI is online. A graphics generating counterpart DALL-E2 is also. I intend to try these out before too long.  Millions use it, including our students!
There are many of them on Internet.

I have tried follows;

AI Restore Old Photos Online
[https://www.aipassportphotos.com/old-photo-restoration](https://www.aipassportphotos.com/old-photo-restoration)
(with water marks)

Restore Old Photos Online To Make Memories Alive
[https://repairit.wondershare.com/online-old-photo-restoration.html?gclid=CjwKCAjwsKqoBhBPEiwALrrqiGKD1kfKzuoWVDCcZ51jWmP0FlnMsya7vn-TyoySQZU4EAliSXm1QhoCSuYQAvD_BwE](https://repairit.wondershare.com/online-old-photo-restoration.html?gclid=CjwKCAjwsKqoBhBPEiwALrrqiGKD1kfKzuoWVDCcZ51jWmP0FlnMsya7vn-TyoySQZU4EAliSXm1QhoCSuYQAvD_BwE)

Free Online Old Photo Restoration
[https://www.capcut.com/tools/old-photo-restoration](https://www.capcut.com/tools/old-photo-restoration)

Restore photos: remove scratches, sharpen colors, and ...
[https://hotpot.ai/restore-picture](https://hotpot.ai/restore-picture)

I think I would go back to my original steps, running GIMP to do the job.  Although it is time consuming but the result is better than using those online AI photo editor

Regards

---

