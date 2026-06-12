---
title: "NVidia graphics and RandRotate in 9.10"
date: 2009-11-05
forum: Multimedia Software
---

### Post by oldsoundguy on 2009-11-05
That's it in a nutshell.  I have NVidia cards in my computers and on a couple of them I have 9.10 that I just installed and Mint 7 on another.  I want to get the screens to rotate to portrait position to be able to do full page editing/composing.
I have such on my main computer, but it is running 8.40LTS and that one has an X11/xorg.conf file that can be edited to include the RandRRotate on option.  NOT SO in 9.10, so where do I go and what do I do to get that effect?
(somewhere I read something about hal replacing xorg, but can't find that anyway!)

---

### Post by oldsoundguy on 2009-11-06
BumpCity!!
Can't believe that someone else has not had and addressed this issue!  It has been around since 8.10.

---

### Post by oldsoundguy on 2009-11-07
Bumpagain!

---

### Post by oldsoundguy on 2009-11-09
I am underwhelmed with the response.  LOL

---

### Post by realzippy on 2009-11-09
Run

**sudo nvidia-xconfig** to get a xorg.conf file to edit as in 8.04

---

### Post by oldsoundguy on 2009-11-09
> **realzippy said:**
> Run

**sudo nvidia-xconfig** to get a xorg.conf file to edit as in 8.04

Command not found

Also ran sudo nano nvidia-xconfig
Blank page

---

### Post by realzippy on 2009-11-09
So not using nvidia-drivers. (?)

---

### Post by oldsoundguy on 2009-11-09
> **realzippy said:**
> So not using nvidia-drivers. (?)

???????  Without Nvida drivers an Nvida card will not work .. be it drivers within the build (default), restricted drivers or those installed with Envy.
In my case, I have the EnvyNG driver package installed as I needed the added screen resolutions. (since Ubuntu no longer can be set up for a specific monitor.)

---

### Post by realzippy on 2009-11-10
> **oldsoundguy said:**
> ???????  Without Nvida drivers an Nvida card will not work .. be it drivers within the build (default), restricted drivers or those installed with Envy.
In my case, I have the EnvyNG driver package installed as I needed the added screen resolutions. (since Ubuntu no longer can be set up for a specific monitor.)

nvidia-drivers means restricted drivers.(The same envyng-script downloads and installs for you).
Of course a nvidiacard would run with vesa drivers....but,back to topic:
**nvidia-xconfig** should work if any restricted-nvidia-graphics-driver is installed.
So,which nvidia driver did envy install?
Is nvidia-settings installed?
Which nvidia-card?
Is there a xorg.conf or is it just (nearly) empty?
If,post it!

---

### Post by oldsoundguy on 2009-11-10
The driver:
Whatever EnvyNG installed

NVidia settings is and has been installed.

Card GEForce 5500 PCI (original Windows software had rotate enable)

NEC 1810x LCD

xorg is totally blank.

---

### Post by realzippy on 2009-11-11
If you edit settings by **gksudo nvidia-settings**,apply and hit the
"Save To Xorg Configuration File" button,what happens?You get a parser error?
If so,delete that empty xorg.conf and run *sudo nvidia-xconfig* again to create a new xorg.conf.Restart X,open nvidia-settings again,change settings,apply,save....

---

### Post by oldsoundguy on 2009-11-11
gksudo nvidia-settings yields the nvidia settings screen with the pop up:
"not using xdriver"

Run sudo apt-get install nvidia-xconfig and get:
"couldn't find package".
Run sudo nvidia-xconfig  and get a "no such file or folder".

---

### Post by realzippy on 2009-11-11
> **realzippy said:**
> So not using nvidia-drivers. (?)

as assumed.

sudo dpkg -reconfigure -phigh xserver-xorg
Nothing?:

Install the driver;something got wrong if used envyng.Why envy?No nvidia-driver in *restricted-drivers* because of old nvidiacard?
Uninstall the driver with envy and reinstall,during installation you are asked for xorg.conf;did you say "yes,configure"?
Which nvidia-driver did envy try to install?

If driver should be installed but not in use due to empty xorg.conf,you could try to use the
8.04 lts xorg.conf file (to avoid damage plug that machines monitor);Section "Monitor","Device","Screen"
would be enough.Mind and delete of course something like *BoardName      "GeForce*willnotfit".
Weird?Maybe your (older) driver **needs** that "[I]Driver         "nvidia""
[/I]

---

### Post by oldsoundguy on 2009-11-11
Well, un-installing and re-installing Envy (173A? driver) got the nvidia xserver to WORK.  But no screen rotate.

So there is now a mini xorg.conf file.

BUT when I re-booted it goes up past the Kbuntu splash screen but not to the Ubuntu splash (have both loaded) nor the sign in .. black screen with blinker in the upper left.  Think I may have to do a total re-install and lose all my tweaks .. (no data loss .. save that off the drive)

YEP, tried the repair and even went into CLI and removed the RandRRotate line.. won't boot to the sign in page.
Doing a clean re-install and will try the Envy FIRST before I start adding my goodies.
Want to  give 9.10 a solid run before I EVER do anything to the machine I am on (it runs 8.40 LTS! and has been virtually flawless since day one.)

Re-install done and installed the EnvyNG package .. got the NVida server to work but no screen rotate.
So went to xorg and added the RandRRotate line as usual. 
Went to re-boot and locked with no display.
Got into CLI again on repair boot and removed the line and it re-booted as it should.

SO, just where can I run the control to rotate?

---

### Post by realzippy on 2009-11-11
Was it:

*Option          "RandRRotation" "on"*

in

*Section "Device"* ?

Have you run nvidia-xconfig and nvidia-settings before?

Could you post the whole xorg.conf ?

---

### Post by oldsoundguy on 2009-11-11
> **realzippy said:**
> Was it:

*Option          "RandRRotation" "on"*

in

*Section "Device"* ?

Have you run nvidia-xconfig and nvidia-settings before?

Could you post the whole xorg.conf ?

Yes on the code line.

Section "Screen"
        Identifier      "Default Screen"
        DefaultDepth    24
EndSection

Section "Module"
        Load    "glx"
        Disable "dri2"
EndSection

Section "Device"
        Identifier      "Default Device"
        Driver  "nvidia"
EndSection


Note that I have the same card on my main computer and am running a cinema display (24") and am able to rotate IT with no problem using the Nvida xconfig screen.
(same driver, also!)(only difference is that the main computer runs 8.40LTS)

---

### Post by realzippy on 2009-11-12
Try this:


Section "Screen"
Identifier "Default Screen"
DefaultDepth 24
EndSection

Section "Module"
Load "glx"
Disable "dri2"    *where is this from?Isn't it only relevant to Intel graphics?*
EndSection

Section "Device"
Identifier "Default Device"
Driver "nvidia"
[COLOR="Lime"]Option	"RandRRotation"   "true"[/COLOR]
EndSection



I asked for *whole* xorg.conf because I was interested in the first (outcommented)  lines.....   ;-)

---

### Post by oldsoundguy on 2009-11-12
you got the WHOLE xorg.conf .. no outcommented lines exist. 
And what you posted is exactly what I did and upon reboot the box locked up after POST to a blank screen with a blinker in the upper left and went NO further. (let it sit that way for an hour!)

Had to re-boot via repair and remove the line.

Upon eventually getting back in found that the entire EnvyNG install had been removed from xorg and had to re-install it.

Minor rant (The ability to rotate the screen was the primary reason I left Fedora and came to Ubuntu 7.40 in the first place.  Then I discovered that the forums for Ubuntu were populated by human beings and not geeks with attitudes, and that sort of settled things on which build I would use! .. but the ability to tweak hardware HAS to be restored to the build for those of us with advanced needs.  Doesn't have to be default, just a door where we can go in and change things more easily!)

There is something in 9.10 that just does not like any alterations to the settings.  This same EXACT setup (with a different monitor) works just fine on 8.40.

If they don't get this right by 10.40, I won't be using it as I had hoped to on my main control computer.)/rant

I am going to take this to the Brainstorm area and I AM going to beta test the next build on one computer to "do my share".

---

### Post by realzippy on 2009-11-12
If you had run nvidia-settings successfully,your xorg would begin with:

# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildd@crested)  Sun Feb  XXXXX UTC 2009

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder58)  XXXXX PDT 2009


You have not done so after installing driver with envyng.
So if your driver now is installed,delete that xorg.conf file from /etc/X11 completely (or rename it).Then run:

**sudo nvidia-xconfig**

what creates a new one which will begin with:

# nvidia-xconfig: X configuration file generated by nvidia-xconfig

Could you do that and post again please?

---

### Post by oldsoundguy on 2009-11-12
done as you asked .. still no commented out lines.

Section "Screen"
        Identifier      "Configured Screen Device"
        DefaultDepth    24
EndSection

Section "Device"
        Identifier      "Configured Video Device"
        Driver  "nvidia"
EndSection

Above is all that shows up in the file.
(we can keep trying, though as this is a test bed computer to make sure stuff works before I accept it as fact!)

---

### Post by realzippy on 2009-11-12
**gksudo nvidia-settings**

change something;e.g. resolution from auto to your monitor's needs,or refresh rate.
Hit "apply" and "Save to X configuration file"
Any changes in xorg.conf?


(important to restart X session after nvidia-xconfig to load new xorg.conf before running nvidia-settings!)

---

### Post by oldsoundguy on 2009-11-12
Won't let me change the primary monitor resolution in nvidia-settings.  (It DOES detect the correct monitor.)

---

### Post by realzippy on 2009-11-12
> **oldsoundguy said:**
> Won't let me change the primary monitor resolution in nvidia-settings.  (It DOES detect the correct monitor.)
Options are only: "auto"?

---

### Post by oldsoundguy on 2009-11-12
> **realzippy said:**
> Options are only: "auto"?

yes

---

### Post by realzippy on 2009-11-12
Then change nothing,Hit "Save to configuration File" .restart (X),what happens to xorg.conf file?

---

### Post by oldsoundguy on 2009-11-12
it won't let me save anything to the configuration file.

I DID try and use the second monitor (which does not exist) and it would save a resolution for it.  But the xorg is the same .. no changes.

(this is kinda NUTS!  Lots of wheel spinning when it could have been solved by making things EASIER, not HARDER to change.  Will hate to see how it reacts when I go to install my Wacom USB pad and try and tweak IT!  THAT is another day (or maybe MONTH)!

---

### Post by realzippy on 2009-11-12
"It won't let me" save anything...
does not help.What does "it" say???

---

### Post by oldsoundguy on 2009-11-12
hit save and nothing happens .. (know that as I restart x  and nothing has changed in the xorg!)  Go back to the nvidia-xconfig and the choice I made is gone.

NO MESSAGE DISPLAYED at any time.

---

### Post by oldsoundguy on 2009-11-13
OK .. Thought this was totally ridiculous that you could get your monitor to rotate, I could get my other set up to rotate, but this one bit it!
So I went back to point A again.
Re-installed 9.10, did the updates, and then set up the Nvidia AGAIN.

IT WORKED THIS TIME.  Now, I have NO CLUE if it was something I did or did not do OR if it was one of the updates that fixed it, but whatever it was, it now works!

Thanks for all your time and really sorry about the frustration it might have caused.

But it just points out what I said before.  I would have had people posting caustic remarks were this the Fedora Forum.  NOT SO here.  Just one of the BEST reasons to use Ubuntu!!

---

