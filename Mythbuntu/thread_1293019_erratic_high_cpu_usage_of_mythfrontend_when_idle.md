---
title: "erratic high cpu usage of mythfrontend when idle"
date: 2009-10-16
forum: Mythbuntu
---

### Post by ryanolf on 2009-10-16
I'm wondering if anyone else notices this problem: mythfrontend has high (well, 15% cpu at 1GHz throttled) when idle on static menus, sometimes. It may start out normal (negligible cpu when idle), but moving around the menus, and then stopping on the same screen selection, cpu usage may get stuck relatively high. It will then stay there for a while, and maybe randomly drop back down later, typically after doing some frontend activity like changing the selection or navigating the menu. The high CPU usage doesn't seem to be linked to particular menu selections, and verbose messages in the terminal don't indicate that mythfrontend is doing anything.

I have noticed this with the mythbuntu and blootube widescreen themes. I'm using OpenGL, but selecting QT didn't seem to change anything. I'm using the latest mythbuntu 9.10 packages. (Here's my --version):

MythTV Version   : 
MythTV Branch    : tags/release-0-22-rc1
Network Protocol : 50
Library API      : 0.22.20091008-1
QT Version       : 4.5.2
Options compiled in:
 linux profile using_oss using_alsa using_pulse using_jack using_backend using_dvb using_firewire using_frontend using_glx_proc_addr_arb using_hdhomerun using_hdpvr using_iptv using_ivtv using_joystick_menu using_libfftw3 using_lirc using_mheg using_opengl_video using_opengl_vsync using_qtwebkit using_v4l using_x11 using_xrandr using_xv using_xvmc using_xvmc_vld using_xvmcw using_bindings_perl using_bindings_python using_opengl using_vdpau using_ffmpeg_threads using_libavc_5_3 using_live using_mheg

Anyone else see something like this? Is this a bug I should file? 15% usage when my CPU is throttled to half it's speed isn't a big deal most of the time, but sometimes I need as much of that CPU as I can get.

---

### Post by jwbrown77 on 2009-10-20
I am seeing the same thing here.  top reports 14% CPU usage on my Mythbuntu 9.10 Beta installation (fully updated).  Nobody is currently using the system, it is just sitting on the main menu.

If I close mythfrontend and reopen, it will be fine for a while, then it starts taking CPU while idling again.

I'd be curious if anyone has figured out what causes this...

---

### Post by jwbrown77 on 2009-10-26
Is no one else seeing this?

I'm wondering if it's something related to the default theme in Mythbuntu 9.10.

It seems like the usage is always high when the system is idling on the menu.  If MythVideo is playing something or if a recording is being played back, the mythfrontend usage goes down to 0.

---

### Post by rrossi on 2010-01-12
I am also seeing this.  Someone suggested turning off OpenGL and use QT instead.  I haven't tried it myself since I'm not at home right now.

---

### Post by rrossi on 2010-01-12
I think I found the solution to this.  The problem was that the TZ environment variable was not set and caused mythfrontend.real to spin on trying to read /etc/localtime.

Once I set TZ, it was fine.

i.e.

export TZ=Canada/Toronto

---

### Post by ZedThou on 2010-01-12
Last night I did an update to the latest 0.22-fixes and noticed an immediate improvement in the responsiveness of the frontend (on an IONITX-A fwiw). The interface was just more snappy and HD channel change times were cut from something like 3-4 seconds to 1-2 seconds. Previously, sitting idle, the frontend would also chew up 12% or so CPU. Now I notice that it's more like 5% at idle.

I wonder if there was a recent change to the fixes branch that cleared up this issue. At any rate, I'm very happy with the sudden improvement.

---

### Post by danbodoh on 2010-01-24
export TZ=US/Central in .bashrc worked wonders for me.  Thanks!

Dan

---

### Post by geekyhawkes on 2010-01-24
Sorry for the probably dumb question, but how do you set the TZ?

---

### Post by geekyhawkes on 2010-01-30
Anyone?

---

### Post by ian dobson on 2010-01-30
Hi,

Just use what editor you feel happy with to edit the file .bashrc in your (user who runs mythfrontend) home directory and add the line 
export TZ=Canada/Toronto 

Or whatever country you have maybe US/Central 

Regards
Ian Dobson

---

### Post by nickrout on 2010-01-30
> **geekyhawkes said:**
> Anyone?

read the post two or three above.

---

### Post by immauss on 2010-12-06
oddly, I've tried adding the TZ export to my .bashrc, .profile, and even added it to the beginning of the /usr/bin/mythfrontend script, but I still have mythfrontend.real hovering at 14-20% CPU almost constantly. 

What am I missing?

---

