---
title: "Gnome-shell on Natty Narwhal"
date: 2010-10-18
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Harry33 on 2010-10-18
I just switched myself to Natty.
I have used Gnome-shell in Maverick, installed from official repos.
It works fine, though the source might be a bit outdated.
Now with the toolchain updated from Natty repos, Gnome-shell works no more.
This is what I get in terminal:

```
 JS ERROR: !!! Exception was: Error: Requiring Clutter, version 1.0: Failed to load typelib file '/usr/lib/girepository-1.0/Clutter-1.0.typelib' for namespace 'Clutter': Typelib version mismatch; expected 4, found 3
    JS ERROR: !!! lineNumber = '0'
    JS ERROR: !!! fileName = 'gjs_throw'
    JS ERROR: !!! stack = 'Error("Requiring Clutter, version 1.0: Failed to load typelib file '/usr/lib/girepository-1.0/Clutter-1.0.typelib' for namespace 'Clutter': Typelib version mismatch; expected 4, found 3")@:0
("Requiring Clutter, version 1.0: Failed to load typelib file '/usr/lib/girepository-1.0/Clutter-1.0.typelib' for namespace 'Clutter': Typelib version mismatch; expected 4, found 3")@gjs_throw:0
@/usr/share/gnome-shell/js/ui/main.js:9
```

Does this mean clutter is too old?

---

### Post by ronacc on 2010-10-18
Natty is still very much pre-alpha , many packages haven't been built/updated yet just keep updating and trying every few days .More packages will probably start coming through after UDS next week .

---

### Post by xebian on 2010-10-18
> **ronacc said:**
> Natty is still very much pre-alpha , many packages haven't been built/updated yet just keep updating and trying every few days .More packages will probably start coming through after UDS next week .

Lucky you UDS is right in your backyard.  Is this open to all or just developers only?

---

### Post by ronacc on 2010-10-18
heck if I know but I'll drop in anyway :lolflag:

---

### Post by castrojo on 2010-10-18
> **xebian said:**
> Lucky you UDS is right in your backyard.  Is this open to all or just developers only?

UDS is always open to the public.

---

### Post by Merk42 on 2010-10-18
I was tempted to make yet another thread here, but I can't even compile it from source in 10.10.```
*** Configuring gdk-pixbuf *** [7/23]
./autogen.sh --prefix /home/merk/gnome-shell/install --libdir '/home/merk/gnome-shell/install/lib64'  --disable-static --disable-gtk-doc 
./autogen.sh: 113: autopoint: not found
*** Error during phase configure of gdk-pixbuf: ########## Error running ./autogen.sh --prefix /home/merk/gnome-shell/install --libdir '/home/merk/gnome-shell/install/lib64'  --disable-static --disable-gtk-doc  *** [7/23]
```

---

### Post by mc4man on 2010-10-18
> compile it from source in 10.10.
./autogen.sh: 113: autopoint: not found

builds ok here (jhbuild
do you have autopoint installed

> ** Configuring gdk-pixbuf *** [7/23]
./autogen.sh --prefix /home/doug/gnome-shell/install --libdir '/home/doug/gnome-shell/install/lib'  --disable-static --disable-gtk-doc 
Copying file ABOUT-NLS
Copying file config.rpath
Copying file m4/codeset.m4
Copying file m4/gettext.m4
.................

---

### Post by ranch hand on 2010-10-18
> **Merk42 said:**
> I was tempted to make yet another thread here, but I can't even compile it from source in 10.10.```
*** Configuring gdk-pixbuf *** [7/23]
./autogen.sh --prefix /home/merk/gnome-shell/install --libdir '/home/merk/gnome-shell/install/lib64'  --disable-static --disable-gtk-doc 
./autogen.sh: 113: autopoint: not found
*** Error during phase configure of gdk-pixbuf: ########## Error running ./autogen.sh --prefix /home/merk/gnome-shell/install --libdir '/home/merk/gnome-shell/install/lib64'  --disable-static --disable-gtk-doc  *** [7/23]
```
I may not be overly fond of GS but I sure hope you get it going and restart your thread.

A testing forum with out that thread is just not quite right.

It is a tradition, respect tradition and git er done.   Please.

---

### Post by xtoudi on 2010-10-19
Yes ... autopoint is another required thing ... just apt-get install autopoint.
This is required since a few weeks :-)

---

### Post by Harry33 on 2010-10-19
> **Harry33 said:**
> I just switched myself to Natty.
I have used Gnome-shell in Maverick, installed from official repos.
It works fine, though the source might be a bit outdated.
Now with the toolchain updated from Natty repos, Gnome-shell works no more.
This is what I get in terminal:

```
 JS ERROR: !!! Exception was: Error: Requiring Clutter, version 1.0: Failed to load typelib file '/usr/lib/girepository-1.0/Clutter-1.0.typelib' for namespace 'Clutter': Typelib version mismatch; expected 4, found 3
    JS ERROR: !!! lineNumber = '0'
    JS ERROR: !!! fileName = 'gjs_throw'
    JS ERROR: !!! stack = 'Error("Requiring Clutter, version 1.0: Failed to load typelib file '/usr/lib/girepository-1.0/Clutter-1.0.typelib' for namespace 'Clutter': Typelib version mismatch; expected 4, found 3")@:0
("Requiring Clutter, version 1.0: Failed to load typelib file '/usr/lib/girepository-1.0/Clutter-1.0.typelib' for namespace 'Clutter': Typelib version mismatch; expected 4, found 3")@gjs_throw:0
@/usr/share/gnome-shell/js/ui/main.js:9
```

Does this mean clutter is too old?
Well I made a bug report on this clutter problem:
Bug # 661698
[https://bugs.launchpad.net/ubuntu/+source/clutter/+bug/661698](https://bugs.launchpad.net/ubuntu/+source/clutter/+bug/661698)

---

### Post by autocrosser on 2010-10-19
OK--finally got all of it to build--won't run with a error I've not seen before:
```
Gtk-Message: Failed to load module "canberra-gtk-module":  libcanberra-gtk-module.so: cannot open shared object file: No such file  or directory
```
The module is in /usr/lib/gtk2.0/modules--I copied it to the main /usr/lib & still no-go.....Ideas anyone?

---

### Post by Mblackwell on 2010-10-20
IIRC that error shows up on most GS instances and shouldn't result in failure.

---

### Post by autocrosser on 2010-10-20
Good to know-I'll do another complete rebuild tonight--must be b0rked somewhere...

---

### Post by xtoudi on 2010-10-20
install libcanberra-dev.

---

### Post by autocrosser on 2010-10-20
> **xtoudi said:**
> install libcanberra-dev.

Checked & it is installed.....will be rebuilding GS within the hour......

---

### Post by xtoudi on 2010-10-21
_**A little advice for everyone:**_

Compile a whole GS ('jhbuild build') **only if needed** (GS require a new libs... etc). 

Usually enough is to compile only gnome-shell module:
```
jhbuild buildone gnome-shell
```

In that way you can save a lot of time and nerves :-)

**_And ... compiling 'datetime' branch._**

In the same way as compiling **overview-relayout** branch you can compile other branch - **'datetime' **- it's very development at this moment but you can see work progress on date/time panel.

About compiling **overview-relayout** (post which I made):

[http://ubuntuforums.org/showpost.php?p=9944930&postcount=813](http://ubuntuforums.org/showpost.php?p=9944930&postcount=813)

and in case of **'datetime'** branch just change step 3 :
```
git clone git://git.gnome.org/gnome-shell -b datetime
```

---

### Post by Mblackwell on 2010-10-21
If you're wanting to test different branches at the same time you can 
```

cd ~/gnome-shell/source/gnome-shell
git checkout <branchname>
git reset --hard HEAD

```
Then all you need to do is the above

```

jhbuild buildone gnome-shell

```

If you're code savvy and know how to work with git I can testify that master, overview-relayout, and datetime can all be merged without much trouble.

---

### Post by Merk42 on 2010-10-21
> **xtoudi said:**
> _**A little advice for everyone:**_

Compile a whole GS ('jhbuild build') **only if needed** (GS require a new libs... etc). 

Usually enough is to compile only gnome-shell module:
```
jhbuild buildone gnome-shell
```

In that way you can save a lot of time and nerves :-)

**_And ... compiling 'datetime' branch._**

In the same way as compiling **overview-relayout** branch you can compile other branch - **'datetime' **- it's very development at this moment but you can see work progress on date/time panel.

About compiling **overview-relayout** (post which I made):

[http://ubuntuforums.org/showpost.php?p=9944930&postcount=813](http://ubuntuforums.org/showpost.php?p=9944930&postcount=813)

and in case of **'datetime'** branch just change step 3 :
```
git clone git://git.gnome.org/gnome-shell -b datetime
```Any idea how to fix the pixbuf errors?
until then I can't build and as such no thread from me, though maybe it's too late for me to make one anyway.

---

### Post by Mblackwell on 2010-10-22
Already said:

sudo apt-get install autopoint

---

### Post by Merk42 on 2010-10-22
> **Mblackwell said:**
> Already said:

sudo apt-get install autopoint

Yay it finally built! It... looks the same?


OKay with that, anyone want me to make my usual thread or no?

---

### Post by cariboo on 2010-10-22
I'd say go ahead.

---

### Post by autocrosser on 2010-10-22
100% YES---I'd say that the changes will be in fairly soon, so just do a copy/paste for now with the current mods--then update when the GUI change happens....

---

### Post by xtoudi on 2010-10-23
> **Merk42 said:**
> Yay it finally built! It... looks the same?


OKay with that, anyone want me to make my usual thread or no?

Master branch looks the same. If you want look at the future you should try 'overview-relayout' branch.

It's good to have complete step by step instruction. Do it (GNOME-SHELL thread):-)

---

### Post by davideotape on 2010-10-23
+1 for the gnome-shell thread :)

---

### Post by davideotape on 2010-10-23
Hmm, getting this error in gtk3:

```
  GISCAN Gtk-3.0.gir
./.libs/libgtk-x11-3.0.so: undefined reference to `gdk_x11_display_set_startup_notification_id'
./.libs/libgtk-x11-3.0.so: undefined reference to `gdk_rgba_get_type'
./.libs/libgtk-x11-3.0.so: undefined reference to `gdk_rgba_to_string'
./.libs/libgtk-x11-3.0.so: undefined reference to `gdk_cairo_set_source_rgba'
./.libs/libgtk-x11-3.0.so: undefined reference to `gdk_rgba_parse'
collect2: ld returned 1 exit status
linking of temporary binary failed: Command '['/bin/bash', '../libtool', '--mode=link', '--tag=CC', '--silent', 'gcc', '-o', '/home/david/gnome-shell/source/gtk3/gtk/tmp-introspect3s8d9U/Gtk-3.0', '-export-dynamic', '-L.', 'libgtk-x11-3.0.la', '-pthread', '-L/home/david/gnome-shell/install/lib', '-lgio-2.0', '-lgobject-2.0', '-lgmodule-2.0', '-lgthread-2.0', '-lrt', '-lglib-2.0', '/home/david/gnome-shell/source/gtk3/gtk/tmp-introspect3s8d9U/Gtk-3.0.o']' returned non-zero exit status 1
make[4]: *** [Gtk-3.0.gir] Error 1
make[4]: Leaving directory `/home/david/gnome-shell/source/gtk3/gtk'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/david/gnome-shell/source/gtk3/gtk'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/david/gnome-shell/source/gtk3/gtk'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/david/gnome-shell/source/gtk3'
make: *** [all] Error 2
*** Error during phase build of gtk3: ########## Error running make   *** [8/23]

```

EDIT: Also getting errors in gconf and gjs

---

### Post by lesnoland on 2010-10-25
for this error do this:

select the "shell" option, then type "make -k install", after that exit and select option 1, and it should work. it seems to be a libtool error.


> **davideotape said:**
> Hmm, getting this error in gtk3:

```
  GISCAN Gtk-3.0.gir
./.libs/libgtk-x11-3.0.so: undefined reference to `gdk_x11_display_set_startup_notification_id'
./.libs/libgtk-x11-3.0.so: undefined reference to `gdk_rgba_get_type'
./.libs/libgtk-x11-3.0.so: undefined reference to `gdk_rgba_to_string'
./.libs/libgtk-x11-3.0.so: undefined reference to `gdk_cairo_set_source_rgba'
./.libs/libgtk-x11-3.0.so: undefined reference to `gdk_rgba_parse'
collect2: ld returned 1 exit status
linking of temporary binary failed: Command '['/bin/bash', '../libtool', '--mode=link', '--tag=CC', '--silent', 'gcc', '-o', '/home/david/gnome-shell/source/gtk3/gtk/tmp-introspect3s8d9U/Gtk-3.0', '-export-dynamic', '-L.', 'libgtk-x11-3.0.la', '-pthread', '-L/home/david/gnome-shell/install/lib', '-lgio-2.0', '-lgobject-2.0', '-lgmodule-2.0', '-lgthread-2.0', '-lrt', '-lglib-2.0', '/home/david/gnome-shell/source/gtk3/gtk/tmp-introspect3s8d9U/Gtk-3.0.o']' returned non-zero exit status 1
make[4]: *** [Gtk-3.0.gir] Error 1
make[4]: Leaving directory `/home/david/gnome-shell/source/gtk3/gtk'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/david/gnome-shell/source/gtk3/gtk'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/david/gnome-shell/source/gtk3/gtk'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/david/gnome-shell/source/gtk3'
make: *** [all] Error 2
*** Error during phase build of gtk3: ########## Error running make   *** [8/23]

```

EDIT: Also getting errors in gconf and gjs

---

### Post by N4zroth on 2010-11-01
Thanks! That worked like a charm (in Maverick, too :-))

---

