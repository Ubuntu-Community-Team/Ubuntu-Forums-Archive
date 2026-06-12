---
title: "XSane error, works - then stops working"
date: 2008-11-10
forum: Multimedia Software
---

### Post by chipw on 2008-11-10
Using XSane 0.995-1ubuntu1 on Hardy Heron 8.04.

I am able to scan a document, maybe two, three or more, then suddenly XSane will quit with this error - 

Failed to start scanner:Error during device I/O

I exit XSane, then I have to unplug the scanner from the wall power, plug it back in, then unplug the usb cable from the pc, then plug it back in, then start XSane, and it works for a while again. Then repeat everything again. My scanner is a Brother MFC-5440CN.

What's going on? Another bug in another ubuntu app?

Well, now it's not working at all, piece of crap. No matter what I do I get this message -
Failed to open device 'brother2:bus2:dev1':error during device I/O

when I try to open XSane. Looks like I have load up the brother drivers on my XP box and finish working on that box because Ubuntu fails me again. :(

---

### Post by ubundom on 2009-04-28
> **chipw said:**
> Using XSane 0.995-1ubuntu1 on Hardy Heron 8.04.

I am able to scan a document, maybe two, three or more, then suddenly XSane will quit with this error - 

Failed to start scanner:Error during device I/O ... snip ... because Ubuntu fails me again. :(

I seem to have had this experience with my wireless HP Photosmart 3300 too. My workaround is to stop trying to use the very feature-rich xsane and I have had success with the much lighter weight skanlite:

```
sudo apt-get-install skanlite
```

I noticed that it uses libksane0, but I do not know whther this is just a KDE thingy.

---

### Post by mkwa on 2009-06-13
I have the same problem with Ubuntu 9.04, xsane, and HP 3300 MFP printer/scanner. The scan starts, gets most (maybe all) of the data from printer to computer, and then xsane puts out an error message box with text 

"Error during read: Error during device I/O" 

and discards the scanned data. Each time this happens, a line is appended to the /var/log/user.log file:

xsane: read_mfpdtf_block timeout cnt=7: scan/sane/pml.c 958

This seems to be a timing issue. I found a workaround:

(1) Start xsane from command line (type xsane and enter).
(2) Do a scan and wait until the progress bar stops at maybe 80% full.
(3) Now freeze xsane by typing ctrl-z (hold down Ctrl key and press z key).
(4) Wait few seconds and unfreeze xsane by typing fg on the command line.

This induced delay fixed the timing issue for me and I got the scanned documents instead of error popups.

---

### Post by davidwhthomas on 2009-08-27
I solved this by running

```
sudo xsane
```

from the terminal and running as root.

You may be able to run as your regular user after following the install instructions here: 

[http://solutions.brother.com/linux/sol/printer/linux/sane_install.html](http://solutions.brother.com/linux/sol/printer/linux/sane_install.html)

---

### Post by bhsu17 on 2009-12-23
Fresh 9.10 install after update

tried sudo xsane and got this:

WARNING: Unhandled message: interface=org.freedesktop.DBus.Introspectable, path=/, member=Introspect

(xsane:1924): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:1924): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:1924): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:1924): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:1924): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:1924): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:1924): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:1924): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:1924): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:1924): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated
The program 'xsane' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
  (Details: serial 15139 error_code 8 request_code 151 minor_code 5)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

any help?

---

### Post by teknotuck on 2012-02-14
Well I just got this same message and searching dragged me here, abviously nobody appears to have resolved it. 
 
 So let me share what I am doing to deal with it, since it might be me again in a few weeks who forgets how I resolved it.

All of these programs use other smaller programs to get their real work done. 

The one program that many of these are using is called scanimage.
Most of you have noticed that as this bug rears its head you do in fact see the image your scanning, you probably even see that the whole image has been scanned and it keeps scanning blank area then bamm! The error pops up, the program closes and .. .nothing is saved!

Ok, so what you can do then is just run it like this, cd into whereever your wanting this image to be saved and run it like this.

scanimage > somefilename.ppm

that will cause it to run but saving its output (full color) into the file your now making called somefilename.ppm

Your probably still going to get the crash because well, its still got a timing issue BUT you will have your scanners results dropped into that file and, well thats all you really wanted anyway right?

Well now you got it. Open it up in gimp or whatever your wanting, crop it save it and keep on doing whatever you need to do.
Hope this helps someone out.

---

