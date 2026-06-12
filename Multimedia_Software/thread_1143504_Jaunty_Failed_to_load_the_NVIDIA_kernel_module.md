---
title: "Jaunty Failed to load the NVIDIA kernel module"
date: 2009-04-30
forum: Multimedia Software
---

### Post by rhm on 2009-04-30
After upgrading to Jaunty I get the following error when booting:

[INDENT]**Ubuntu is running in low-graphics mode**
The following error was encountered. You may need to update your configuration to solve this.
(EE) NVIDIA(0): Failed to load the NVIDIA kernel module!
(EE) NVIDIA(0): ***Aborting***
(EE) Screen(s) found, but none have usable configurations.[/INDENT]

After that it gives me an option to run in low graphics mode for just one session, reconfigure graphics, troubleshoot the editor or exit to console. Reconfiguring graphics leaves me in the same situation, and the other two options aren't helpful (to me) so I enter in low-graphics mode.

Once there, a gray box pops up in front of a blue screen. It reads:
[INDENT]There already appears to be a X server running on display:0. Should another display number be tried?[/INDENT]
I accept the option and it gives a new warning:
[INDENT]The specified display number was busy so this server was started on display 1.[/INDENT]

This finally leaves me at the login screen in 800x600 resolution. After logging in, I cannot access the NVIDIA X Server Settings and running nvidia-xconfig as suggested by it does not yield any different results upon reboot.

I originally asked for help in this thred:
[http://ubuntuforums.org/showthread.php?p=7174072#post7174072]("http://ubuntuforums.org/showthread.php?p=7174072#post7174072")

In this thread you will find the last adjustments to my video drivers before the upgrade:
[http://ubuntuforums.org/showthread.php?t=1129280]("http://ubuntuforums.org/showthread.php?t=1129280")

---

### Post by ausmuso on 2009-04-30
You should always be in text mode when doing this kind of thing, rhm.

Go to a console in text mode by hitting  ( Ctrl+Alt+F1 ). Login as usual.
Next you must stop the X-server by entering:
  sudo /etc/init.d/gdm stop && sudo killall Xorg

Now you can run your NVIDIA install script or whatever else you were planning to do.

Good luck.

---

### Post by inobe on 2009-04-30
show me what nvidia components are installed.


we may need to go back to nvidia 180.44.

so we want to disable the avenard source and remove anything 180.51 !

when removing the module and components check to make sure it doesn't take your desktop with it, meaning review what gets removed.

if some components give you problems' restart and go back for them later.


you will notice later the 180.44 drivers replacing the 180.51's, so basically the 51's have to be removed in order to see the 44's.


it's a backwards step.

it appears that i am taking you in an odd direction but i think this will work for you.

you may still need to run nvidia xconfig

---

### Post by rhm on 2009-04-30
> **inobe said:**
> show me what nvidia components are installed.



Here's a screen shot from Synaptic, with the install components. Was there a way to get this list using the command line?


> **inobe said:**
> we may need to go back to nvidia 180.44.

so we want to disable the avenard source and remove anything 180.51 !


The avenard source was ``disabled on upgrade to Jaunty''. The line is still in the Third-Party Software tab of the Repositories list of Synaptic, but it's unchecked and has the quoted warning as a name.

I'll wait for your input before I start removing anything.

---

### Post by rhm on 2009-04-30
I'm also getting a new error when trying to load X. It says:
[INDENT]The greeter application seems to be crashing[/INDENT]
or something along those lines. I am sure it's related to all of this, but can't understand why it is happening now and not from day one. After a few tries it will either lock me out for two minutes or let me log in.

---

### Post by inobe on 2009-04-30
just what i thought.

start removing anything 180.51.

as i said before' review what gets removed before removing "very important"

apparently it looks like modealiases.

---

### Post by inobe on 2009-04-30
yes remove nvidia-180.51-modealiases 


restart


open synaptic and install nvidia-180.44-modealiases


go hardware drivers' enable the driver and restart.


go to system> administration> nvidia settings...

if it gives you the nvidia xconfig error' run it in terminal

restart

---

### Post by rhm on 2009-04-30
Just removed the nvidia-180.51-modealiases. It took with it nvidia-common.
Will restart now.

---

### Post by inobe on 2009-04-30
after restarting tell me whats all listed 180.51

---

### Post by rhm on 2009-04-30
After rebooting, it locked me out for two minutes. Once inside, I went to Synaptic, looked for [FONT="Lucida Console"]nvidia-180.44-modealiases[/FONT] but only found [FONT="Lucida Console"]nvidia-180-modealiases[/FONT], which I installed.

Then I went to Hardware Drivers and there were no Nvidia drivers listed, so I rebooted, waited the mandatory two minutes and came back to Hardware Drivers. It still doesn't list any Nvidia drivers.

I'm stumped here. What do we do now?

---

### Post by inobe on 2009-04-30
don't worry were doing good, go in and search nvidia common.

or at least whats listed here

nvidia-settings
nvidia-180-kernel-source
nvidia-common
nvidia-180-modealiases
nvidia-glx-180
jockey-common
jockey-gtk

---

### Post by inobe on 2009-04-30
here's what i have installed.

[IMG]http://www.itsyourpc.org/duane/files/nvidia_installed.jpg[/IMG]

ignore the other driver versions and focus on 180

---

### Post by rhm on 2009-04-30
I was missing nvidia-common, so I installed it. Rebooted (two-minutes, etc. it's getting old). 

Nvidia drivers now show up in the Hardware Drivers menu. I attempted to activate the 180 driver but the progress dialog would just pop up and immediately out. This happened several times, so I opted for the 177 driver, for the sake of trying. This one downloaded and activated. I gave the 180 driver a last shot before rebooting and it (magically) worked.

I'm about to reboot again.

---

### Post by inobe on 2009-04-30
i think were getting somewhere, remember to go to nvidia settings to see if it requests running nvidia xconfig !

---

### Post by rhm on 2009-04-30
Rebooted. Went to Nvidia X Server Settings and it requested nvidia-config + restart X. Ran sudo nvidia-config and everything seemed to work OK. Ctrl+Alt+Backspace doesn't seem to work, so I rebooted again. Same string of errors as before.

After logging in, I went back to Nvidia X Server Settings and nothing had changed.

---

### Post by inobe on 2009-04-30
then we are missing a required components.

let's go back into synaptic and search nvidia without filters and tell me if all those components are installed.


i have a gut wrenching feeling that's the current trouble.

---

### Post by rhm on 2009-04-30
It turned out that I had all the required components, but all the relevant drivers were 180.44. Apparently there was a conflict between my video card and the 180.44 drivers.

**Solution:**
With the help of Inobe, we decided that updating everything to the Nvidia 180.51 drivers would be the best course of action (or that, at any rate, it couldn't make things much worse).

Guided by Inobe, I repeated the process laid out here: [http://ubuntuforums.org/showthread.php?t=1129280]("http://ubuntuforums.org/showthread.php?t=1129280") which implied: 
[LIST=1]
[*]Enabling the Avenard repository that had been disabled on upgrade by Jaunty (Synaptyc -> Settings -> Repositories -> Third-Party Software)
[*]Reloading the repositories
[*]Updating via Update Manager (or sudo apt-get update on terminal)
[*]and rebooting.
[/LIST]

After reboot, everything worked as it should (even Compiz).

Many thanks to Inobe, who has been helping me troubleshoot this for the past four hours. You are great.

---

### Post by inobe on 2009-04-30
your welcome rhm :)


no disrespect to the forums but i needed to pull rhm off and get him live, however under the agreement that he include the fix in the forums.

that's the fix and no harm done.

hope this solution works for more people.

enjoy

---

### Post by latefee on 2009-05-01
Forum suggestions were helpful but unproductive for me.  However, I was able to get my card to work by installing the latest driver from Nvidia: ([http://www.nvidia.com/object/linux_display_amd64_185.18.04.html](http://www.nvidia.com/object/linux_display_amd64_185.18.04.html))

Had to drop into CTRL-F1 level and stop GDM but once run the script it installed the driver without problem and so far seems to be working.

---

### Post by inobe on 2009-05-02
the original objective to this thread was to use terminal only once or not at all.

i save command line as last resort, in fact i can't stress that enough.

---

### Post by wjstarck on 2009-05-02
Inobe-

A thousand and one thanks for your solution. I had been unable to get nvidia driver (GeForce 7600GS) working since the upgrade to Intrepid. Now it all works perfectly, even Compiz.

The only thing extra not shown here I needed to do was add the line 

Modes          "1024x768"

under Subsection Display like so

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "1024x768"
    EndSubSection
EndSection

Again, thank you!

---

### Post by d4v1dv00 on 2009-05-20
> **rhm said:**
> It turned out that I had all the required components, but all the relevant drivers were 180.44. Apparently there was a conflict between my video card and the 180.44 drivers.

**Solution:**
With the help of Inobe, we decided that updating everything to the Nvidia 180.51 drivers would be the best course of action (or that, at any rate, it couldn't make things much worse).

Guided by Inobe, I repeated the process laid out here: [http://ubuntuforums.org/showthread.php?t=1129280]("http://ubuntuforums.org/showthread.php?t=1129280") which implied: 
[LIST=1]
[*]Enabling the Avenard repository that had been disabled on upgrade by Jaunty (Synaptyc -> Settings -> Repositories -> Third-Party Software)
[*]Reloading the repositories
[*]Updating via Update Manager (or sudo apt-get update on terminal)
[*]and rebooting.
[/LIST]

After reboot, everything worked as it should (even Compiz).

Many thanks to Inobe, who has been helping me troubleshoot this for the past four hours. You are great.

Hi there, i follow the instruction above and when i select upgrade of "nvidia-glx-180" it prompts to uninstalled gnome-desktop, .... a list of vital components... how?

---

### Post by rhm on 2009-05-20
You don't want to uninstall the gnome desktop or other vital components. At which point does it ask you to uninstall? If possible, unselect the non-Nvidia components so that *only* the Nvidia components are uninstalled.

---

### Post by meannickgreen on 2009-06-15
Hi guys- 

I'm having the exact same problem that he's describing in the beginning of this thread, only one major difference - I need a little more assistance with the steps.

I tried to upgrade from 8.04 to 8.10 to Jaunty all at once (in one sitting), and I'm getting the exact same messages he is. I also have an Nvidia card. Everything was working perfectly before the attempted upgrade.

I'd list the config file here, but I'm not sure how to copy paste from the inoperative computer over to this laptop that I'm typing on now. Maybe there are certain areas that are of more interest that I can just type in.

I'd love to try some of the ideas presented here, but I'm not sure how, and need some exact commands...

Help? :confused:

---

### Post by rhm on 2009-06-16
> **meannickgreen said:**
> Hi guys- 

I'm having the exact same problem that he's describing in the beginning of this thread, only one major difference - I need a little more assistance with the steps.

I tried to upgrade from 8.04 to 8.10 to Jaunty all at once (in one sitting), and I'm getting the exact same messages he is. I also have an Nvidia card. Everything was working perfectly before the attempted upgrade.

I'd list the config file here, but I'm not sure how to copy paste from the inoperative computer over to this laptop that I'm typing on now. Maybe there are certain areas that are of more interest that I can just type in.

I'd love to try some of the ideas presented here, but I'm not sure how, and need some exact commands...

Help? :confused:

Take a look at the solution post: [http://ubuntuforums.org/showthread.php?p=7188733#post7188733]("http://ubuntuforums.org/showthread.php?p=7188733#post7188733"). It will require a bit of reading, but the instructions are clearly laid out (I would know... I followed them :)). I'll be around for a while, if you have any specific questions.

---

### Post by agm_ultimatex on 2009-08-05
> **inobe said:**
> here's what i have installed.

[IMG]http://www.itsyourpc.org/duane/files/nvidia_installed.jpg[/IMG]

ignore the other driver versions and focus on 180

I grabbed what you have, and I have a 9800gt, similar issues. Seems to work so far :)

---

### Post by aspa on 2009-08-27
For me the same symptoms got fixed when I installed the linux-headers package.

---

### Post by mackerman on 2009-08-27
I also have the same issues with an Nvidia 7600 GT.  I have followed all of the steps in this thread and the solution thread (adding the 3rd party repositories for the new driver) and still have no solution.  One thing that was different in my trials was when the drivers showed up in "Hardware Drivers" (after adding nvidia-common) when I clicked Activate, they would download and look like they installed, but after this they did not show activated.

I then tried installing the latest Nvidia driver from: [http://www.nvidia.com/object/linux_display_ia32_185.18.36.html]("http://www.nvidia.com/object/linux_display_ia32_185.18.36.html")

I had to go to console session & kill gdm & killall Xorg.  Then the installer ran and gave me the following error messages:
```
-> Installing NVIDIA driver version 185.18.36.
-> No precompiled kernel interface was found to match your kernel; would you li
   ke the installer to attempt to download a kernel interface for your kernel f
   rom the NVIDIA ftp site (ftp://download.nvidia.com)? (Answer: Yes)
-> No matching precompiled kernel interface was found on the NVIDIA ftp site;
   this means that the installer will need to compile a kernel interface for
   your kernel.
-> Performing CC sanity check with CC="cc".
-> Performing CC version check with CC="cc".
ERROR: Unable to find the kernel source tree for the currently running kernel. 
       Please make sure you have installed the kernel source files for your
       kernel and that they are properly configured; on Red Hat Linux systems,
       for example, be sure you have the 'kernel-source' or 'kernel-devel' RPM
       installed.  If you know the correct kernel source files are installed,
       you may specify the kernel source path with the '--kernel-source-path'
       command line option.
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  
```
Any advice is appreciated.

---

### Post by finni on 2009-09-11
> **aspa said:**
> For me the same symptoms got fixed when I installed the linux-headers package.

Installing linux-headers package worked for my machine (Geforce 9400) too! Couple hours lost on this thing. :)

---

