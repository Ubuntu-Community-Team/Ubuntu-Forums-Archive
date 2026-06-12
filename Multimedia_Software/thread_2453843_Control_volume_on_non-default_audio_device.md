---
title: "Control volume on non-default audio device"
date: 2020-11-17
forum: Multimedia Software
---

### Post by neodimiummagnet on 2020-11-17
I'm running Xubuntu 18.04, but I imagine this should apply to any version. I have a setup where I'm running my headphones off a USB DAC/amp, and a set of speakers off the internal audio. I'd like to keep the USB DAC with a built in volume knob as the default audio device for opened applications, but I'd also like to always control the internal audio from my keyboard's volume wheel. Is there any way to go about achieving this?

---

### Post by wildmanne39 on 2020-11-17
*Thread moved to **Multimedia Software for a more appropriate fit**.*

---

### Post by CatKiller on 2020-11-18
I think it's doable, but not *easily* doable.

The audio streams for applications are going to open on the default device, and the displayed volume control - which is what's going to be controlled by media keys - is the currently selected device. The assumption is going to be that those are generally the same, and if there's only one volume control exposed that's either going to be the default one, or the one that most recently got an audio stream assigned to it.

There are probably ways to automatically route audio streams to a non-default device, so that your volume controls don't affect them, but you'd still run the risk that the volume controls would follow the streams to the device you don't want to control.

So the easiest way, I'd say, to do what you want, is to play around with **amixer** to find the commands to increase or decrease the volume of the specific device you're interested in by the amount that you want, and then assign keybindings to those commands to your volume up / volume down controls.

---

### Post by neodimiummagnet on 2020-11-18
That's not a bad solution and I'd be happy with it, but my volume keys don't want to take the new assignments. They're XF86 keys, and seem to be stuck controlling the default audio device. I tried both the xfce application shortcuts menu, and xmodmap binding to set them to something else first.

---

### Post by CatKiller on 2020-11-18
Sorry, I don't know what else to suggest to break that linkage other than what you've already tried. Maybe someone that uses Xfce will chime in with something.

---

### Post by neodimiummagnet on 2020-11-18
I might end up creating a new thread about this specific issue actually. The multimedia keys are grabbed by something before any custom key bindings can work. I can see the key codes using the keycode command, but xev doesn't give me codes for these keys. If I can get this fixed then my volume control question can also be considered solved.

---

