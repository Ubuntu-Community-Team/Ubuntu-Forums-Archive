---
title: "sn9cX webcam problem"
date: 2010-11-23
forum: Multimedia Software
---

### Post by dkavraal on 2010-11-23
I still have the common problem with a SN9C120 webcam (with brand "Lemon Webcam"). The point is I have discovered this log in Xorg.0.log:

> (II) config/udev: Adding input device sonixj (/dev/input/event4)
(**) sonixj: Applying InputClass "evdev keyboard catchall"
(**) sonixj: always reports core events
(**) sonixj: Device: "/dev/input/event4"
(II) sonixj: Found keys
(II) sonixj: Configuring as keyboard
(II) XINPUT: Adding extended input device "sonixj" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "evdev"
(**) Option "xkb_layout" "tr"

It is ridiculous that it thinks I have a "keyboard" connected rather than a "webcam" :)

Is there a way to overcome this obstacle?

Thanks.






**For interested parties here are the other info:**

> 
# uname -a
Linux hostname 2.6.34-02063405-generic #201008211111 SMP Sat Aug 21 12:15:42 UTC 2010 i686 GNU/Linux
# cat /etc/issue
Ubuntu 10.04.1 LTS



> # lsusb
Bus 003 Device 002: ID 045e:0039 Microsoft Corp. IntelliMouse Optical
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 008: ID 0c45:613c Microdia PC Camera (SN9C120)
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

also /etc/X11/xorg.conf if needed:
> Section "Device"
	Identifier	"Configured Video Device"
	Driver		"intel"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "Module"
	Load "intel"
EndSection

Section "Monitor"
        Identifier "External Monitor"
        Option "DPMS"
        HorizSync 30.0-86.0
        VertRefresh 50.0-160.0
        modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
        modeline "1024x768@100"  113.31  1024 1096 1208 1392  768 769 772 814  -hsync +vsync
        [...]
EndSection

Section "Screen"
        Identifier "External Screen"
        Monitor "External Monitor"
        DefaultDepth 24
        Option "metamodes" "1280x960 102.1 1280 1360 1496 1712 960 961 964 994"
        SubSection "Display"
        Depth 24
        Modes "1280x960_60.00"
        EndSubSection
EndSection


and dmesg:

> [ 4512.736066] usb 2-2: new full speed USB device using uhci_hcd and address 8
[ 4512.900890] gspca: probing 0c45:613c
[ 4512.907651] sonixj: Sonix chip id: 12
[ 4512.909111] input: sonixj as /devices/pci0000:00/0000:00:1d.0/usb2/2-2/input/input12
[ 4512.909253] gspca: video0 created
[ 4512.909258] gspca: found int in endpoint: 0x83, buffer_len=1, interval=100


the funny thing; when I click the "shoot" button on the webcam here is the outcome in dmesg:
> [ 4778.511712] atkbd serio0: Unknown key pressed (translated set 2, code 0x55 on isa0060/serio0).
[ 4778.511727] atkbd serio0: Use 'setkeycodes 55 <keycode>' to make it known.



> #lsmod

video                  19453  1 i915
output                  1843  1 video
videodev               38237  1 gspca_main
v4l1_compat            13648  1 videodev


---

### Post by no2498 on 2010-11-24
lsusb don't see it as a keyboard 


just try the cam in the program cheese
if you need to push a key do it  and try cheese

its full name is cheese webcam booth look in sound&video for it first
if not installed

sudo apt-get install cheese

---

### Post by dkavraal on 2010-11-24
sorry not to add them symptom. I have already tried cheese. I have black screen (not a dark picture; it's just whole black --see below). 

I tried to change properties in gstreamer-properties and nothing differs. When I use the button "try" in gstreamer-properties for the "v4l2" option, no picture is seen.

edit: Now here is a new sympthom I have seen:
> # sudo cat /dev/video0
cat: /dev/video0: Input/output erro


From cheese:
Main window (while cam is open)
[IMG]http://tinypic.com/r/2wbt84l/7[/IMG]
Preferences (cam is selected as seen)
[IMG]http://tinypic.com/r/uxzl3/7[/IMG]

GStreamer Properties:
[IMG]http://tinypic.com/r/1zgucyq/7[/IMG]



(links for the images if needed anyhow: [http://tinypic.com/r/2wbt84l/7](http://tinypic.com/r/2wbt84l/7) [http://tinypic.com/r/uxzl3/7](http://tinypic.com/r/uxzl3/7) [http://tinypic.com/r/1zgucyq/7](http://tinypic.com/r/1zgucyq/7))

---

### Post by dkavraal on 2010-11-24
I have just upgraded to 10.10 because I couldn't make/build any package due to absence of headers (which anyhow I couldn't install).

So I tried Kylea Baker's gspca package as refers at [http://kyleabaker.com/2010/07/12/microsoft-lifecam-vx-1000-linux-gspca-patch/](http://kyleabaker.com/2010/07/12/microsoft-lifecam-vx-1000-linux-gspca-patch/). But nothing yet. Still:

> # cat /dev/video0 
cat: /dev/video0: Input/output error

---

