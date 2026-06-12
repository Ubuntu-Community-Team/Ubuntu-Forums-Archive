---
title: "Gimp + wacom = no mouse, problem"
date: 2011-01-12
forum: Multimedia Software
---

### Post by ac3raven on 2011-01-12
So I successfully configured my wacom CTL-460 for Ubuntu 10.04, and it works great except when I'm in Gimp.  I can use my tablet in Gimp, but only after I open gimp and restart it several times.  And on top of that, if I want to use my mouse for something in Gimp, I can't.  I try to select tools with my mouse and nothing happens, I try to drag a selection box around using the mouse and nothing happens.  My mouse is for some reason not interacting with Gimp at all.  This started happening after I installed the tablet.  What could it be?

---

### Post by ragtag on 2011-01-12
I use Gimp and Wacom (Intuos, CintiQ and TabletPC) regularly in 10.04 without any problems, so it should work. I haven't tried the Bamboo tablets, but I can't imagine they're that different from the Intuos.

How did you configure your wacom? In 10.04 you no longer need to mess with xorg.conf, to get it working. You still need to Configure Extended Inputs in the GIMP preferences, setting them to screen.

The only problem I've had with it is when I change the rotation of the screen on my tablet pc, I need to restart GIMP to get the pen to map correctly.

---

### Post by ragtag on 2011-01-12
On my workstation, that's using a Cintiq, I have the following in /etc/hal/fdi/policy/custom_wacom.fdi

```

<?xml version="1.0" encoding="UTF-8"?> <!-- -*- SGML -*- -->
<deviceinfo version="0.2">
  <device>
    <match key="input.x11_driver" contains="wacom">
      <match key="input.x11_options.Type" contains="stylus">
	<merge key="info.product" type="string">stylus</merge>
        <merge key="input.x11_options.KeepShape" type="string">on</merge>
        <merge key="input.x11_options.PressCurve" type="string">15 0 100 85</merge>
      </match>
      <match key="input.x11_options.Type" contains="eraser">
	<merge key="info.product" type="string">eraser</merge>
        <merge key="input.x11_options.KeepShape" type="string">on</merge>
        <merge key="input.x11_options.PressCurve" type="string">15 0 100 85</merge>
      </match>
      <match key="input.x11_options.Type" contains="pad">
	<merge key="info.product" type="string">pad</merge>
        <merge key="input.x11_options.KeepShape" type="string">on</merge>
      </match>
      <match key="input.x11_options.Type" contains="cursor">
	<merge key="info.product" type="string">cursor</merge>
        <merge key="input.x11_options.KeepShape" type="string">on</merge>
      </match>
    </match>
  </device>
</deviceinfo>

```

None of this does anything really important though. It's just changing some basic settings, that you would previously have done in xorg.conf.

Is it possible that you've enabled too much in the GIMP Extended Input dialog. On my TabletPC, I get things like 'Virtual core XTEST pointer' and 'SynPS/2 Synaptic Touch Pad', which you just want to leave in Disabled mode. It's only the Wacom Tablet, Stylus and Eraser you should enable here.

Of course, it's possible that your problem is Bamboo specific, so I'm sorry I can't be of any more help. :)

p.s. Have you tried it in other programs that support pressure, like MyPaint, Krita, Blender, InkScape and others.

---

### Post by odd on 2011-05-31
Quite old topic, but I can confirm that mouse is not working (in Gimp, Inkscape, MyPaint, but works in Blender, so GTK apps only affected I guess) when USB tablet (mine is Intuos3) is connected :(. Interestingly, in some cases it starts working again, but I can't reproduce it (I haven't tried to unplug/replug tablet (it's not a solution).

Note: When I launch MyPaint, mouse works for some time (few clicks), then stops (in terminal, "device change: Core Pointer <enum GDK_SOURCE_MOUSE of type GdkInputSource>" appears // launch MyPaint from terminal//).
I'm using git version of xf86-input-wacom (0.11 I guess), Ubuntu Lucid 64bit.

---

### Post by odd on 2011-05-31
And here we have a workaround:
It seems that when you use eraser (at least once) in Gimp for example, mouse starts working again (in Inkscape and so on as well).

---

