---
title: "Can't set default image viewer to command line (it resets to default)"
date: 2018-12-18
forum: Multimedia Software
---

### Post by when-updtae on 2018-12-18
Default image viewer is awful. When I try loading ~5000x5000 photo which is only ~10 mb it is super slow and slows down whole ubuntu OS. I want it to be imagemagick because it worked great from command line.
I right click my .jpg, "propeties", open with: "set", user command, new window opens, I enter "display %u" and hit "ok".
"open with" now shows nothing (empty box) and when I open my image, it still opens with default laggy image viewer and freezes whole ubuntu os.
what do i do
EDIT. Found out that %u can't process non-latin characters. how to fix

---

### Post by ajgreeny on 2018-12-18
Just delete the %u from the command as it's not needed, as far as I'm aware.

I think from what you say that the program you are trying to use is one of the binary executables of imagemagick-6.q16, **/usr/bin/display-im6.q16**, so you may need to try using the full executable pathway.

However, both **display** and **display-im6** are links to the actual executable **display-im6.q16** so any of them should work in a command.

Just try any of those three without the %u to see if that's successful.

---

### Post by when-updtae on 2018-12-19
It still resets to default for some reason

---

### Post by ajgreeny on 2018-12-19
Have a look at the file **.local/share/applications/mimeapps.list** in a text editor and search for the word **image** which should show which applications are set as potential ones to open the image files you want, eg jpg, png etc etc.
 
You can, I believe, edit that file if you wish to change the applications you want to open different filetypes, but back it up first so you can restore it if necessary..

---

### Post by mc4man on 2018-12-19
You can't do it with that command, that's for a .desktop file.
You can try
```
display "$1"
```

Other options would be to create a bash script using above command & place in a bin folder in your $PATH
You could also, if desired, create a .desktop, using either above command or  the script on the Exec= line. (- and add %u to end of line..

---

