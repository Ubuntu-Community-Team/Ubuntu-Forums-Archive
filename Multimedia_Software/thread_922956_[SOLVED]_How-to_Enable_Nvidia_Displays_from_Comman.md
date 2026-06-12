---
title: "[SOLVED] How-to: Enable Nvidia Displays from Command Line"
date: 2008-09-17
forum: Multimedia Software
---

### Post by redmoskito on 2008-09-17
I have a Lenovo Thinkpad T61, and I had been trying to find a way switch between monitors using a keystroke.  Particularly, this meant finding a way to enable/disable monitors using the command line.

[This thread ]("http://ubuntuforums.org/showthread.php?t=909301") suggested that nvidia-settings should make this possible, but apparently, it isn't implemented by Nvidia, yet...  (or so the "TODO" section of [this document]("ftp://download.nvidia.com/XFree86/Linux-x86/nvidia-settings-user-guide.txt")) suggests)

Luckily, we can compile the nv-control-dpy tool, which will give us the tools we need to enable or disable monitors, with a little extra help from scripts I wrote.  

First, lets get the source code.  


```

$ mkdir nvidia-source
$ cd nvidia-source
$ apt-get source nvidia-settings
$ cd nvidia-settings-*

```

Next, download dependencies

```

$ sudo apt-get install build-essential libxext-dev libx11-dev

```

First, you have to compile the an nvidia library:

```

$ cd src/libXNVCtrl
$ make

```

Now, build nv-control-dpy:

```

$ cd ../../sample
$ make nv-control-dpy

```

If all went well, you should have an executable nv-control-dpy file in your directory.  This application lets us perform many of the low-level operations that nvidia-settings performs when you use it from the GUI interface.  

   Test it out:

```

$ ./nv-control-dpy -h

```

Let's install this executable somewhere convenient:

```

$ sudo cp nv-control-dpy /usr/local/bin

```

I have written some bash scripts to parse the output of nv-control-dpy, and some command-line php scripts to do to the enabling and disabling operations (because my Perl-fu is weak :) ).  These files are attached to this post.    

To install the scripts:

```

$ tar xzvf nv-tools.tar.gz
$ cd nv-tools
$ sudo cp -r scripts/* /usr/local/bin

```

Included scripts:
[LIST]
[*]nv-get-displays - list the currently attached displays
[*]nv-get-metamodes - list metamodes in a format easily consumable by my php scripts
[*]nv-get-current-metamode - get the id of the currently attached metamode
[*]nvidia/nvidia.inc.php - functions for parsing metamodes and switching between modes.
[/LIST]

You can control these by writing a simple command-line php script.  The "sample/" subdirectory has a few examples of how to enable a single monitor, or enable multiple monitors.  Here's an example of enabling a CRT monitor at 1280x1024 resolution:

[PHP]
#!/usr/bin/php5
<?
require_once('/usr/bin/nvidia/nvidia.inc.php');

enable_single_display('CRT-0', "1280x1024");
[/PHP]

Note: you'll need to change /usr/bin/php5 to wherever your command-line php interpreter is located.  Also, you may wish to locate the nvidia.inc.php file elsewhere in your filesystem, so update the require_once line if you do

To enable multiple monitors, use the following syntax:

[PHP]
#!/usr/bin/php5
<?
require_once('/usr/bin/nvidia/nvidia.inc.php');

$displays = array(
    'DFP-0' => '1280x800',
    'CRT-0' => '1280x1024'
);

enable_displays($displays);
[/PHP]

Now, you can just make these scripts executable, and [assign them to a key-combination]("http://www.howtogeek.com/howto/ubuntu/assign-custom-shortcut-keys-on-ubuntu-linux/").


If you are interested in how this all works, it goes something like this:  For a specific configuration, you have to create a "metamode" using nv-control-dpy which says which monitors are enabled, at what resolution, and at what location relative to one another.  The command is: "nv-conrol-dpy --add-metamode <meta-modeline>" .  Once you've created a metamode, nv-control-dpy will assign it an id. Using the xrandr utility you can switch to this new configuration by specifying the display resolution and specifying the id as the framerate.  Nvidia uses the framerate to store the id, because there is no simple way distinguish two different configurations that have the same resolution in xrandr.  The resolution you give to xrandr is the total size of the virtual screen made up of all enabled monitors (e.g. if I have a 1280x1024 monitor cloned with a 1440x900 monitor, the resolution would be 1440x1024).

---

### Post by nickzeff on 2008-10-07
Thanks for this post!

Instead of using PHP, I coded what I needed into a bash script. If you're interested it's here:

[http://ubuntuforums.org/showthread.php?t=940932](http://ubuntuforums.org/showthread.php?t=940932)

Cheers!

---

### Post by ZManODS on 2008-10-10
This works great but after changing my display resolution with xrandr the gnome-panel will stretch across both monitors. Also, If I maximize a window it will stretch across both screens!

Is there anyway to have gnome-panel just stretch across the main monitor? If I save my configuration and reboot my computer I will have both monitors working AND the gnome-panel will be correctly on just one screen. 

Is there anyway I can have this behave after using xrandr?

---

### Post by swatkins on 2009-01-02
I found a very easy way to switch between both monitors to a single monitor, using xorg.conf and xrandr. It's described here:

  [http://ubuntuforums.org/showthread.php?p=6480694](http://ubuntuforums.org/showthread.php?p=6480694)

Sam

---

