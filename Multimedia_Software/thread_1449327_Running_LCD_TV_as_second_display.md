---
title: "Running LCD TV as second display"
date: 2010-04-07
forum: Multimedia Software
---

### Post by attercop on 2010-04-07
I've been searching for a bit of advice on how to get my Samsung LCD TV set up as an occasional second display for watching videos from my laptop. I'm connecting from the laptop HDMI out to the TVs HDMI in.

I don't think TwinView is what i want to do, because from what i understand that assumes each display is half of the whole. What i'd like is to just have the TV as the display when it's plugged in, or at least have it mimic the laptop display.

I'm using Ubuntu 9.10 and a Nvidia G210M on the latest Nvidia 195 proprietary driver. Connection is HDMI to HDMI.

Any advice would be great.

---

### Post by NT4usB on 2010-04-08
iirc, TwinView gives you one desktop on two displays. 
fwiw, I use nvidia-settings to set up two xscreens. Then I have two distinct desktops. Mouse journeys between the two but apps launch on one or the other...

---

### Post by vsfiles on 2010-04-11
I have the same problem with Sony Vaio nvidia gefore g210m and TV Philips via HDMI. Do you khow how to create second screen in nvidia settings? I see only one laptop screen in X server configuration.

---

### Post by attercop on 2010-04-20
Hopefully Nvidia will include more options in their proprietary Linux driver in future. To allow us to better use things like HDMI outs. I'm currently running version 195.36.15 and it doesn't yet work as i'd like it to.

---

### Post by NT4usB on 2010-04-20
> **vsfiles said:**
> ...Do you khow how to create second screen in nvidia settings?...
Not without being in front of my box.
iirc, there's a button to add another xserver or some such.
I rarely use nvidia-settings. Only when building a new box, then only to get a base xorg.conf. Then I work direct in xorg.conf and fine tune stuff.

ed: ok, so under X server display configuration there's a configure button>separate xscreen.

---

### Post by elphaba on 2010-04-21
I'm using a vga connection to my LCD TV and not HDMI.  I have been successful by running nvidia-settings (or in my case I've created a launcher) making sure I have privileges (I use sudo) and select twinview and clicked on the "samsung" box (this is the brand of TV I have which means mine is recognized by nvidia, yours would be whatever brand you are running.)  When I click on or select the samsung box, the outline becomes red . I configure "position" as "clones", clicked on "apply" and (I think I saved settings) - anyway the "clone" config worked perfectly.

---

### Post by attercop on 2010-04-21
> **elphaba said:**
> I'm using a vga connection to my LCD TV and not HDMI.  I have been successful by running nvidia-settings (or in my case I've created a launcher) making sure I have privileges (I use sudo) and select twinview and clicked on the "samsung" box (this is the brand of TV I have which means mine is recognized by nvidia, yours would be whatever brand you are running.)  When I click on or select the samsung box, the outline becomes red . I configure "position" as "clones", clicked on "apply" and (I think I saved settings) - anyway the "clone" config worked perfectly.
That's quite interesting, because my TV is also a Samsung one, and i also tried to configure it using the method described above. I got as far as setting up the TV using the TwinView option, but later when i unplugged the HDMI cable and went back to using the laptop screen found that X was broken for that screen so i had to go back to my original xorg.conf from a backup. Where abouts is the option for a "Clone" of the screen? I can only see Disabled, Separate X, or TwinView as the options available.

---

### Post by elphaba on 2010-04-21
I've attached a screenshot of the nvidia settings. "Clones" MUST be set for this to work.  The default on mine is "absolute" and everytime I run nvidia-settings now, it will default to that so I need to reset it before I leave the nvidia-settings config app. Hope I'm explaining this right and that this helps. (I don't need to run it very often, only like now to document what is going on for myself and others.)

I wonder if you aren't seeing "position" as an option to change. Maybe you aren't running nvidia-settings with admin privilege.  I found I couldn't run nvidia from the applications menu.  I had to go to a terminal session and run it. 
  Once in a terminal session, I entered at the prompt: sudo nvidia-settings and it will prompt you for your admin password - it is only at this point I was able to do the right configuration so that it would remain even after I exited nvidia-settings.

(I also learned this the hard way since it wasn't obvious when I was running nvidia from the app menu that I didn't have the privilege I needed to actually make the config change from this point -- only from the term session running sudo nvidia-settings)

---

### Post by attercop on 2010-04-27
That was good advice and i'm grateful. It's helped me get a lot further in my attempts than before. By running gksu nvidia-settings i was able to get the clone screen going on my LCD TV.

Unfortunately i'm still getting problems with the software and configuration. Even as root from a terminal a bug in nvidia-settings means you can't save to X.

And despite using a HDMI cable i could only get video to work on the LCD TV without sound. The only sound was coming from the laptop speakers.

---

### Post by elphaba on 2010-04-27
Glad the info I posted on nvidia was helpful.

I installed some usb speakers on my laptop and went through some troubleshooting before I was successful configuring PulseAudio correctly.
Are you using PulseAudio? (If not, maybe you need to install it?)

If so, you first need to determine what info is returned when you enter the following command in a terminal session:
cat /proc/asound/cards 
and see if you can get the system description of your hdmi audio

And also, next enter:
cat /etc/modprobe.d/alsa-base 
and determine if your hdmi audio (description of which you got from command above) might be commented out with a #.  This means it is being prevented from being the default.  You want to remove the # - maybe more mods but I need to find my documentation (that I created for myself) if you need more info.

There is some other stuff but these are the two most important things.  Rebooting is also necessary at some point plus some other changes to pulseaudio settings.  Let me know if you want more info from me. But if so, I'd like to have a screen capture from you regarding the results from commands above.

Let me know.

---

