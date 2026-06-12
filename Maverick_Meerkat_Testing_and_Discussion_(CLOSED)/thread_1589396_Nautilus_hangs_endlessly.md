---
title: "Nautilus hangs endlessly"
date: 2010-10-06
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by JackNocturne on 2010-10-06
I upgraded from Ubuntu 10.04 to 10.10 RC two days ago. When i rebooted, and logged in,,
all my desktop contents were gone,lots of programs couldn't launch and nautilus hangs forever (cannot access any folder).

Output of Nautilus -c gives
[HTML]Gtk-Message: Failed to load module "canberra-gtk-module": libcanberra-gtk-module.so: cannot open shared object file: No such file or directory

(nautilus:8593): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(nautilus:8593): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(nautilus:8593): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(nautilus:8593): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(nautilus:8593): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(nautilus:8593): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(nautilus:8593): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(nautilus:8593): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(nautilus:8593): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(nautilus:8593): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(nautilus:8593): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(nautilus:8593): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(nautilus:8593): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(nautilus:8593): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",
Gtk-Message: Failed to load module "gnomesegvhandler": libgnomesegvhandler.so: cannot open shared object file: No such file or directory
running nautilus_self_check_file_utilities
running nautilus_self_check_file_operations
running nautilus_self_check_directory
running nautilus_self_check_file
running nautilus_self_check_icon_container
running nautilus_self_check_file_utilities
running nautilus_self_check_file_operations
running nautilus_self_check_directory
running nautilus_self_check_file
running nautilus_self_check_icon_container
[/HTML]murrine and canberra gtk engines are installed.

I tried some suggestions such as deleting .gnome2,.gnome2_private,.nautilus and .config from ~/ ,nothing helped.

Strangely firefox can launch and that's what im using to write this with.  

Any help/suggestions to solve this are appreciated.

---

### Post by ronacc on 2010-10-06
open a terminal and run
```
 sudo apt-get --fix-broken 
```
and see what happens . If that don't help try switching to a different theme , your problem seems to be your theme is broken and GTK can't draw most of the desktop .

---

### Post by JackNocturne on 2010-10-06
thanks for the reply,

From the command you suggested i got the following as output;

```
sudo apt-get install --fix-broken
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```I tried changing to **different **themes, problem remained,it only changed the **error** to "**respective**" theme engine.

Couple of other stuff i tried


[LIST]
[*]making a new user ,problem was the same
[*]opening nautilus with **sudo** [WORKS] but crashes as soon i drag or do some other things
[*]If for instance want to open **software-center** ,it fails to open and output of ~/.xsession-errors is [PHP]Initializing nautilus-gdu extension

(nautilus:7145): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
nautilus: symbol lookup error: nautilus: undefined symbol: gtk_widget_send_focus_change
Traceback (most recent call last):
  File "/usr/bin/software-center", line 29, in <module>
    import gtk
  File "/usr/lib/pymodules/python2.6/gtk-2.0/gtk/__init__.py", line 40, in <module>
    from gtk import _gtk
ImportError: /usr/lib/pymodules/python2.6/gtk-2.0/gtk/_gtk.so: undefined symbol: gtk_viewport_get_view_window
[/PHP]
[/LIST]
I'm stuck, dont know what exactly is the problem:(

---

### Post by kahumba on 2010-10-06
If you're interested into a working desktop rather than hacking the OS I'd suggest doing a clean install of the RC or a daily build.

---

### Post by JackNocturne on 2010-10-06
true, but im saving that for the **last** effort when i'm 90% sure there is no way to fix it without losing my sanity

---

### Post by ronacc on 2010-10-06
ok here are a couple of other things to try . 1st check your /etc/apt/sources.list and make sure everything did get updated to maverick . then open a terminal and run .

```
 sudo apt-get update 
```
then 
```
sudo apt-get upgrade 
```
then
```
sudo apt-get dist-upgrade 
```

if you used update-manager to do the original upgrade from 10.04>10.10 theres a good chance that not everything upgraded properly , update-manager is not the best thing to use during developement .

---

### Post by JackNocturne on 2010-10-07
hi again,

i checked my /etc/apt/sources.list ,it was ok.

I typed all those commands at terminal to update,upgrade then dist-upgrade, [COLOR=Black]it said there is nothin to upgrade and that all upgrades have been done.

[/COLOR]

---

### Post by ronacc on 2010-10-07
Hmm apt obviously thinks everything is updated , have you looked in /usr/lib/gtk-2.0/modules to see if libcanberra-gtk-module.so  is really there and in /usr/lib/gtk-2.0/2.10.0/engines  to see if murrine is there ? also try installing a different theme engine .

---

### Post by JackNocturne on 2010-10-07
> **ronacc said:**
> Hmm apt obviously thinks everything is updated , have you looked in /usr/lib/gtk-2.0/modules to see if libcanberra-gtk-module.so  is really there and in /usr/lib/gtk-2.0/2.10.0/engines  to see if murrine is there ? also try installing a different theme engine .

hello,
output of ls /usr/lib/gtk-2.0/modules```
libatk-bridge.so           libferret.so      libgail.so
libcanberra-gtk-module.so  libgail-gnome.so  libgnomesegvhandler.so

```and of /usr/lib/gtk-2.0/2.10.0/engines ```
libclearlooks.so   libindustrial.so  libnodoka.so     libthinice.so
libcrux-engine.so  libluaengine.so   libpixmap.so
libglide.so        libmist.so        libredmond95.so
libhcengine.so     libmurrine.so     libsvg.so

```They are there, what would cause them** not **to be detected? Could this be a bug or just configuration mistake?

---

### Post by ronacc on 2010-10-07
It probably is a config error , going back to your first post it is saying it can't locate the theme engine in the "module_path" , unfortuntely I don't know where that path is stored , look around in gconfig-editor and see if you can find anything there .

---

