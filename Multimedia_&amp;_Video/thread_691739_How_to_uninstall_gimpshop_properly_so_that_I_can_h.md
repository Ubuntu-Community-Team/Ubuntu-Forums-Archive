---
title: "How to uninstall gimpshop properly so that I can have both versions side by side"
date: 2008-02-08
forum: Multimedia &amp; Video
---

### Post by streamsanddragonflies on 2008-02-08
I hope this is the best place to post.  I finally found the right way to install gimpshop after unpacking the archives in a ~folder which I cd to in terminal and typed

 " wget -c http://www.plasticbugs.com/blogimg/gimpshop_2.2.11-1_i386.deb"

only to discover in the included install doc. which reads:

GIMP 2.2 replaces GIMP 2.0. It is advised that you **uninstall GIMP 2.0**
before installing GIMP 2.2. If you want to keep GIMP 2.0 installed in
parallel to GIMP 2.2, you have to[B] choose a separate prefix which is
not in your default library search path[/B].

I **did not uninstall gimp first**!  and apart from the splashpage, I seem to have the same gimp 2.0 exept I had to add a temp and swap file for this version.  I wanted both GIMPS in parallel so I think I should de-install and start over.

Is uninstalling gimpshop in synaptic enough?  Or are there extra commands in terminal to add?

Also, could I have an example of how and where** (proper path)** to write the **separate prefix** so that both gimps can co-exist?  I am feeling nooby about this!!


Gimp is coming out with version 2.4 with "easy installer" soon.  So I want to be able to upgrade the standard gimp pkg. only.
Also, the install doc. for Gimpshop, recommends all these packages and file versions that are not installed in my synaptic or debian pkgs. For example:

" You need to have installed GTK+ version 2.4.4 or better. Do not
     try to use an older GTK+ version (1.2.x), it will not work.
     GTK+ itself needs recent versions of GLib (>= 2.4.5),
     Pango (>= 1.4.0) and ATK. Sources for these can be grabbed from
     [ftp://ftp.gtk.org/](ftp://ftp.gtk.org/). GTK+-2.x and friends can be installed side
     by side with GTK+-1.2."

In synaptic, I only have Gtk-2 engines and libgtk-2.0 common among other related files, but no version GTK+  2.4.4 anywhere, so  should I assume that if I don't have the latest versions, I can't access all the features of gimpshop?!

**Note**:  I wonder if opening the deb pkg. with GDebi Package Installer is the equivalent to  "wget -c http://www.plasticbugs.com/blogimg/gimpshop_2.2.11-1_i386.deb" in terminal?

---

