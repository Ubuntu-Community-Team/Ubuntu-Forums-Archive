---
title: "Natty Alpha 3 - Mountall: disconnected from Plymouth"
date: 2011-03-12
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by dwigyit on 2011-03-12
After upgrading to Natty Narwhal alpha 3, I get the splash screen (displayed improperly, but I guess that's a different issue) then, instead of continuing with the boot, I get a black screen with 
"Mountall: disconnected from Plymouth" printed at the top in white. Sometimes, various errors are displayed before it, but not always, and they often vary, and the text can flicker (refresh) a few times too.

I have a feeling it's related to my ATI graphics driver, as I have tried this install twice. The first time, I installed a fresh copy of the alpha from a USB and it booted fine several times - but then I installed the driver from the ATI website and it started showing this error afterwards. The second time, I wiped Natty and installed 10.10 (I also installed the ATI driver from the Additional Drivers tool whilst still on 10.10), then upgraded to Natty using distribution upgrade. It started giving this boot error streight away.

Please help, as I need to use 11.04 to properly contribute Unity-related articles to the ubuntu tour project (can't write guides for it if I can't run it :( ).

---

### Post by Iowan on 2011-03-12
Moved to Natty Narwhal Testing and Discussion.

---

### Post by Harry33 on 2011-03-12
> **dwigyit said:**
> After upgrading to Natty Narwhal alpha 3, I get the splash screen (displayed improperly, but I guess that's a different issue) then, instead of continuing with the boot, I get a black screen with 
"Mountall: disconnected from Plymouth" printed at the top in white. Sometimes, various errors are displayed before it, but not always, and they often vary, and the text can flicker (refresh) a few times too.

I have a feeling it's related to my ATI graphics driver, as I have tried this install twice. The first time, I installed a fresh copy of the alpha from a USB and it booted fine several times - but then I installed the driver from the ATI website and it started showing this error afterwards. The second time, I wiped Natty and installed 10.10 (I also installed the ATI driver from the Additional Drivers tool whilst still on 10.10), then upgraded to Natty using distribution upgrade. It started giving this boot error streight away.

Please help, as I need to use 11.04 to properly contribute Unity-related articles to the ubuntu tour project (can't write guides for it if I can't run it :( ).

Uninstall the proprietary ATI driver, it does not support the xserver 1.10 rc2 in Natty.
Xserver 1.10 final will soon be uploaded into Natty repos too.

See also that you have these open source drivers installed:
- xserver-xorg-video-ati
- xserver-xorg-video-radeon
- xserver-xorg-video-vesa

---

### Post by dwigyit on 2011-03-12
Fair enough - can that be done through the Ctrl-Alt-F2 terminal?

---

### Post by coffeecat on 2011-03-12
> **dwigyit said:**
> Fair enough - can that be done through the Ctrl-Alt-F2 terminal?

If you installed the proprietary ATI drive from their website, there should be an uninstall script, mentioned in the link below. There may be some other things to check when reverting to the open source ATI driver, described in the link:

[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver)

What card do you have? Unity works just fine with the open source driver with both my Radeon HD4350 desktop and Mobility Radeon HD4200 laptop.

---

### Post by dwigyit on 2011-03-12
HD5870

And on my current install, it was installed on Maverick (before the upgrade) from the Additional Drivers program. I guess it wasn't removed automatically (probably something I should submit as a bug report :) ).

---

### Post by coffeecat on 2011-03-12
> **dwigyit said:**
> HD5870

And on my current install, it was installed on Maverick (before the upgrade) from the Additional Drivers program :)

OK. The link gives instructions for uninstalling the fglrx driver wherever it came from. :) I'll be interested to hear how well the Natty version of the OS ati driver works with your card.

---

### Post by dwigyit on 2011-03-12
I tried the first method described in the link. It all went fine up until reinstalling the fglrx-modaliases package, for which is says there is no install candidate then fails. Same happens if I just do apt-get install (without the --reinstall. I can quote the exact error if you need it.

I did all the other steps in the first section, but now it simply shows a blank screen after the splash and the CTRL+ALT+F2 command doesn't work. I can only get a terminal now by going in as root using the recovery option in GRUB.

---

### Post by dwigyit on 2011-03-13
On the plus side, the splash screen now perfectly fits the monitor, which it never did before. Too bad it freezes black afterwards...

The exact error I get when trying the reinstall command on Fglrx-modaliases is:

```

Package fglrx-modaliases is not available, but is referred to by another package. This may mean that the package is missing, has been obsoleted, or is only available from another source
However, the following packages replace it:
Fglrx

E: Package 'fglrx-modaliases' has no installation candidate

```

---

### Post by Harry33 on 2011-03-13
> **dwigyit said:**
> I tried the first method described in the link. It all went fine up until reinstalling the fglrx-modaliases package, for which is says there is no install candidate then fails. Same happens if I just do apt-get install (without the --reinstall. I can quote the exact error if you need it.

I did all the other steps in the first section, but now it simply shows a blank screen after the splash and the CTRL+ALT+F2 command doesn't work. I can only get a terminal now by going in as root using the recovery option in GRUB.

There is no fglrx-modialases package in Natty repos.
You should not install it anyway.
Fglrx does not support Natty's xserver.

---

### Post by jennybrew on 2011-03-13
I can sympathise with the OP as graphics are very hit and miss per se and I _now know_ that problems with the Plymouth process are very common indeed.
I used to think it was just me!
A trawl through Launchpad would suggest numerous issues around this process have been reported and as far as I can see remain largely unresolved.

---

### Post by dwigyit on 2011-03-13
Then what do I do to fix the problem I have?

---

### Post by coffeecat on 2011-03-13
> **jennybrew said:**
> I can sympathise with the OP as graphics are very hit and miss per se

If you mean in Natty, then that's an over-generalisation. Except for some older chipsets, most Intel graphics are giving a good Unity experience with 3d. Ditto for those ATI cards which are well-supported by the open source driver. I'm delighted by how well Unity/compiz works with my two ATI cards and the OS driver.

The open source nouveau nvidia driver is a less happy story, but only because, unlike with Intel and ATI, it has had to be developed without the help of the manufacturer. It's coming along though.

The proprietary ATI and nvidia drivers are a mess (in Natty) at the moment, but they always have been in previous releases  at this stage of development. They are proprietary drivers where the OS community has no control. But they usually appear in time for final release.

> **jennybrew said:**
> I _now know_ that problems with the Plymouth process are very common indeed.

Only with proprietary graphics drivers.

---

### Post by dwigyit on 2011-03-14
So how can I get around the error given by coffecat's fix and get Ubuntu booting again?

---

### Post by jennybrew on 2011-03-14
> **dwigyit said:**
> So how can I get around the error given by coffecat's fix and get Ubuntu booting again?

Well with all respect to coffeecat I can only restate that a trawl through Launchpad would suggest numerous issues around this  process, prior to and during Natty development, have been reported and as far as I can see remain largely  unresolved.

Having said that I do agree that the Intel drivers seem reasonably stable. Unfortunately the same cannot be said of ATI drivers and NVidia drivers ...open source or otherwise.

Hopefully someone can offer a workaround to your problem but the real answer is for the bugs to be fixed.

---

### Post by dwigyit on 2011-03-14
So I can't just uninstall the ATI one through the terminal then?

Ah well... I guess it's time for a third Natty reinstall :D

---

### Post by coffeecat on 2011-03-14
> **dwigyit said:**
> So I can't just uninstall the ATI one through the terminal then?

Ah well... I guess it's time for a third Natty reinstall :D

Do you mean uninstall the proprietary driver - the fglrx? I thought you'd done that. 'ATI' usually refers to the open source driver.

Have you tried running the latest daily live? See if that works. If it does so without the black screen issue you are encountering at least you'll know a default install with the open source driver and your particular card works. Perhaps your HD5870 isn't as well supported as my earlier chipset by the open source driver, but I'd be surprised. I'm sure I read somewhere that the 5*** series is supported - at least in theory.

---

### Post by Harry33 on 2011-03-15
> **coffeecat said:**
> Do you mean uninstall the proprietary driver - the fglrx? I thought you'd done that. 'ATI' usually refers to the open source driver.
...
Perhaps your HD5870 isn't as well supported as my earlier chipset by the open source driver, but I'd be surprised. I'm sure I read somewhere that the 5*** series is supported - at least in theory.

I have heard several booting issues with this very same AMD's high-end HD5870 card (Evergreen Cypress).
xserver-xorg-video-ati (v. 6.14.*) should support it.
Anyway, in all cases I have read, there have been messing with fglrx involved, either using .run file from AMD or Jockey of Natty (.deb file); in worst cases, all of them are mixed.

---

### Post by coffeecat on 2011-03-15
> **Harry33 said:**
> Anyway, in all cases I have read, there have been messing with fglrx involved

**Off-Topic Warning**. 

I've seen many threads (for pre-Natty releases) where the OP has been prompted by Jockey to install the fglrx driver where their card is perfectly well served by the open source driver (except perhaps for gaming). Conditioned by the Windows way of working, no doubt, the OP has read the prompt as meaning  they **must** install the proprietary driver. They have done so, and then profoundly regretted it.

I really think for ATI cards the Jockey prompt should state: "An alternative proprietary driver is available. This may be useful if you require the sort of 3-d acceleration that games need. Be warned, though, that it may also cause you a level of pain, frustration and anguish which you, innocent soul, do not deserve."

:wink:

---

### Post by zika on 2011-03-15
> **coffeecat said:**
> **Off-Topic Warning**. 

I've seen many threads (for pre-Natty releases) where the OP has been prompted by Jockey to install the fglrx driver where their card is perfectly well served by the open source driver (except perhaps for gaming). Conditioned by the Windows way of working, no doubt, the OP has read the prompt as meaning  they **must** install the proprietary driver. They have done so, and then profoundly regretted it.

I really think for ATI cards the Jockey prompt should state: "An alternative proprietary driver is available. This may be useful if you require the sort of 3-d acceleration that games need. Be warned, though, that it may also cause you a level of pain, frustration and anguish which you, innocent soul, do not deserve."

:wink:I've read Your post with a sort of déjà vu... I think similar suggestion was made quite some time ago... On the spot...

---

### Post by Harry33 on 2011-03-15
> **coffeecat said:**
> 
...
I really think for ATI cards the Jockey prompt should state: "An alternative proprietary driver is available. This may be useful if you require the sort of 3-d acceleration that games need. Be warned, though, that it may also cause you a level of pain, frustration and anguish which you, innocent soul, do not deserve."


This is a good idea. :P

---

### Post by dwigyit on 2011-03-15
I noticed that in Natty, the Additional Drivers tool didn't show the propriatary driver that shows in Maverick, so would I be right in assuming that there is a list of working drivers for each seperate version of Ubuntu? If only the distro upgrate tool checked to make sure that all the installed Maverick drivers were still compatible with Natty before the upgrade, the problem I had (and presumably that other have) would be avoided? Maybe it's something that can be changed - perhaps a little warning box which gives you the option to remove the incompatible drivers before the upgrade continues.

---

### Post by jennybrew on 2011-03-15
> **coffeecat said:**
> **Off-Topic Warning**. 

Conditioned by the Windows way of working, no doubt, 



*sigh* 

We would do a lot better for proprietary drivers if Linux provided a stable ABI (Binary Interface) for driver developers to develop against.

---

### Post by ranch hand on 2011-03-15
> **coffeecat said:**
> 
Only with proprietary graphics drivers.
I beg to differ with you.  Plymouth is another reason (Unity is the other) that I now use Debian.

Plymouth, if I keep "quiet in my instruction string, will boot and better yet, eventually, shut down.

As boot manager it is supposed to log the errors but there have never been any logged at all.

Plymouth, in spite of the heroic efforts of the Ubuntu devs, is just not up to use on diverse hardware.

Hopefully the OP will not have this problem on the final release.

---

### Post by ranch hand on 2011-03-15
> **dwigyit said:**
> I noticed that in Natty, the Additional Drivers tool didn't show the propriatary driver that shows in Maverick, so would I be right in assuming that there is a list of working drivers for each seperate version of Ubuntu? If only the distro upgrate tool checked to make sure that all the installed Maverick drivers were still compatible with Natty before the upgrade, the problem I had (and presumably that other have) would be avoided? Maybe it's something that can be changed - perhaps a little warning box which gives you the option to remove the incompatible drivers before the upgrade continues.
It is a good idea when upgrading, particularly to a testing version, to remove all proprietary drivers.  It is a habit that many of us, that have been on this ride before, just have and never think to mention.

---

### Post by Harry33 on 2011-03-15
> **ranch hand said:**
> It is a good idea when upgrading, particularly to a testing version, to remove all proprietary drivers.  It is a habit that many of us, that have been on this ride before, just have and never think to mention.

Exactly this. Also it is a very good practice to uninstall additional PPA's too.
Especially those regarding X (like xorg-edgers).

It is one good thing to remember that proprietary drivers usually do not support any newly released development versions of xserver either.

---

### Post by jennybrew on 2011-03-15
> **Harry33 said:**
> Exactly this. Also it is a very good practice to uninstall additional PPA's too.
Especially those regarding X (like xorg-edgers).
It is one good thing to remember that proprietary drivers usually do not support any newly released development versions of xserver either.

Totally agree, Ive always tried not to have any proprietary drivers. However, and reinforced by your final sentence, if Linux would present a stable ABI for third party / proprietary driver developers, we would see an enormous improvement in driver support for Linux. I guess that would involve a major rethink in terms of philosophy as well as system design though :)

---

### Post by cariboo on 2011-03-15
This seems to come up every release, keep in mind that the graphics card manufacturers also contribute to Xorg-xserver, they know what is coming way before the latest release. nVidia for example had drivers ready to go before the last Xorg-xserver upgrade was released.

For me on all three systems running nVidia cards everything works as it should using the restricted drivers, Plymouth works, I don't have any of the glitches that I have when running nouveau.

I can't speak for ATI/AMD, as I refuse to use their hardware, but they've always been slow to release new drivers.

---

### Post by recluce on 2011-03-16
I have been getting the same error:

- "wrong" boot screen
- message at the end of the boot process "Mountall: disconnected from Plymouth"

However, my system shares only one similarity with the OP's: I run kernel 2.6.38 (2.6.38-5 at the moment, to be precise). Other than that, everything is different: I have Nvidia 270.29 drivers and I am not even running Natty (Lucid here).

While I get the same error message, the boot does complete on my system and I have no further issues.

The similarities on such different systems would imply that this actually might be a kernel issue.

---

### Post by Harry33 on 2011-03-16
> **recluce said:**
> I have been getting the same error:

- "wrong" boot screen
- message at the end of the boot process "Mountall: disconnected from Plymouth"

However, my system shares only one similarity with the OP's: I run kernel 2.6.38 (2.6.38-5 at the moment, to be precise). Other than that, everything is different: I have Nvidia 270.29 drivers and I am not even running Natty (Lucid here).
...


Your "Lucid" is not a default Lucid any longer.
You are using Natty dev version kernel and nvidia-current.

PS. You can try upgrading kernel to the 2.6.38-7 stable release.

---

### Post by recluce on 2011-03-19
> **Harry33 said:**
> Your "Lucid" is not a default Lucid any longer.
You are using Natty dev version kernel and nvidia-current.

PS. You can try upgrading kernel to the 2.6.38-7 stable release.

I know that my Lucid installation is not "stock", but that is unimportant for the point I was trying to make: just about everything in my system is different from the OPs system, except the kernel - implying that a kernel problem could be (just "could") the source of the error.

BTW: installed -7 kernel through the ppa yesterday, no change.

---

