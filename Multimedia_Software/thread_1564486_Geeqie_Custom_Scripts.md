---
title: "Geeqie Custom Scripts"
date: 2010-08-30
forum: Multimedia Software
---

### Post by Bynack on 2010-08-30
Hello all,

Hoping someone can help me. I'm trying to write a bash script to run from Geeqie. So I created a .desktop in Geeqie and pointed at by script. The .desktop file looks like this:

[Desktop Entry]
Version=1.0
Type=Application
Name=Test

# call the helper script
TryExec=/home/andrew/Documents/systemsetup/programs/test.sh
Exec=/home/andrew/Documents/systemsetup/programs/test.sh %f

# Desktop files that are usable only in Geeqie should be marked like this:
Categories=X-Geeqie;
OnlyShowIn=X-Geeqie;

# Show in menu "test"
X-Geeqie-Menu-Path=EditMenu

# It can be made verbose
# X-Geeqie-Verbose=true

MimeType=image/jpeg;

I made both the .desktop and .sh file executable. When I save this file and go back to the main window in Geeqie I can't find any link/launcher to run the script.

Any ideas greatly appreciated. 

Cheers

Andrew :confused:

---

### Post by jobano on 2010-09-20
I had the same issue!!

Your script appears to be good, place it under
~/.local/share/applications/
and it will appear in the Edit menu of Geeqie ;)

---

