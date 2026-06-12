---
title: "Getting ATI Rage Pro to work with Ubuntu 7.04"
date: 2008-01-02
forum: Multimedia &amp; Video
---

### Post by cmoreland on 2008-01-02
Hello, I am running Ubuntu 7.04 on a Gateway Solo Pro 9300 which uses an ATI Rage Mobility P/M and my OpenGL is horribly slow. It's using the default ATI driver used with a fresh install. 

Is there a way to increase video performance? Can I use the fglrx driver with this? I've tried setting my depth to 16 instead of 24 but it has had minimal effect.

---

### Post by esteckis on 2008-01-02
ATI has released a new driver dated 12/20.

There is also another post to install the ATI driver,
Envy site [http://albertomilone.com/nvidia_scripts1.html]("http://albertomilone.com/nvidia_scripts1.html")

1/3/08 **The NEW Envy program installed the new ATI dated 12/20/07 driver and special effects and compiz both work. The only thing with the new ATI driver for me is the screen slightly flickers when the screen saver is running.  Out of 12 times of trying to get the ATI installed, special effects to take and Compiz working, this NEW ENVY version worked for me.**

ATI 1250 series onboard video using UBUNTU Gutsy 64 bit version

---

### Post by Yellow Pasque on 2008-01-02
> Also, ATI has released a new driver dated 12/20.

fglrx is not going to support the Rage/Pro. It only supports the Radeon 9500 or later

---

### Post by cmoreland on 2008-01-02
Hmm, the fglrx driver has zero support for Rage? That's a bummer, I don't see any other way to get OpenGL support.

---

### Post by Yellow Pasque on 2008-01-02
Tried this driver?
[http://gatos.sourceforge.net/ati.2.php](http://gatos.sourceforge.net/ati.2.php)

---

### Post by cmoreland on 2008-01-03
Well I had a look at the ati.2 driver but I'm using X.org not XFree86. So I downloaded the ati.4.4.0: X.org 6.7.0 driver and unpacked it but my xorg.conf file still shows the old 'ati' driver. So I don't think anything changed. (I restarted X using CTRL-ALT-BACKSPACE)

Back to the drawing board?

---

### Post by Yellow Pasque on 2008-01-03
> **cmoreland said:**
> Well I had a look at the ati.2 driver but I'm using X.org not XFree86.
Back to the drawing board?

You are using Xfree86 (yes, it's in the form of "X.org"). So try that driver.
> In February 2004, with version 4.4.0, The XFree86 Project adopted a license change that the Free Software Foundation considered GPL incompatible. Most Linux distributions found the potential legal issues unacceptable and made plans to move to a fork from before the license change. At first there were multiple forks, but the X.Org fork soon became the dominant one. Most XFree86 developers who were already annoyed at other issues in the project also moved to X.Org.--http://en.wikipedia.org/wiki/XFree86

---

### Post by cmoreland on 2008-01-03
Ok, I will try the 4.3.0 driver, I know to unpack it in /usr but do I also need to do anything else once I have unpacked it? Regarding the drm kernel that is listed with the ati.2 driver, where should I unpack it? I have looked over the instructions and they are pretty vague, maybe I'm just not understanding the basics here.

---

