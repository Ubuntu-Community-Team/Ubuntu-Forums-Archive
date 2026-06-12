---
title: "conflicting fb hw"
date: 2010-08-09
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by buzzmandt on 2010-08-09
getting this message in the kernel logs almost every time, but not every time.  when this happens desktop effects and video performance is terrible.  Any help would be greeted favorably.

```
conflicting fb hw usage inteldrmfb vs VESA VGA - removing generic driver
```

Maverick testing
Kubuntu
Kde 4.5.0

---

### Post by Catharsis on 2010-08-09
If I remember correctly, this is a harmless message that's just a symptom of the X driver taking over the framebuffer from the vesa fb (which is loaded first). So they're both loaded at the same time, and then the vesa fb is kicked by the intel one.

The fact that you're getting regressed performance when it shows is very odd though. I'd check /var/log/Xorg.0.log and see if a different driver is loaded in these situations, etc.

---

### Post by buzzmandt on 2010-08-09
I think you're right actually, however with more testing this and thats i have found that if desktop effects are enabled when i log in they are very bad laggy, jerky, slow. If I disable them then reenable them they work fine.... interesting.  Possibly a KDE issue?

---

### Post by Catharsis on 2010-08-10
It might be. I'm assuming you're using Intel graphics?

I know there are a lot of problems in both Compiz and KDE for the intel graphics stack, so it's not incredibly surprising that you're having problems with both of them together.

If I were you, I'd wait for the X Server 1.9 upgrade to land (see the sticky for details) and then reassess. I know the kernel team is doing some tweaking with the framebuffers in Maverick, but I thought that all landed already (but I might be mistaken; I haven't been following it very carefully).

---

### Post by x-shaney-x on 2010-08-10
I have the same boot message on my maverick install which appears EVERY time.
I have also seen the same boot message on a couple of other distros if splash is turned off.
I did file a bug report on it and was told it is simply a message telling you it is doing exactly what it says, handing off the framebuffer handling and would normally be hidden by the splash.

Regarding the desktop effects, I believe that problem is completely unrelated to the boot messages.

I get the message on regular ubuntu install which has no problems with desktop effects.
AFTER I installed kubuntu-desktop (and later installed from a kubuntu maverick iso) I found desktop effects are appallingly slow and clunky.

I did get a dramatic improvement (but not brilliant) by enabling Desktop effects > Advanced > Use Vsync

For reference here is the bug report: [https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/609044](https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/609044)

---

