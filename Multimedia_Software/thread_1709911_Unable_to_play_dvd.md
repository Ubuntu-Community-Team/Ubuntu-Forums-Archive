---
title: "Unable to play dvd"
date: 2011-03-19
forum: Multimedia Software
---

### Post by AnupamMitra on 2011-03-19
I placed the DVD in the player's window. Movie Player was installed earlier. When I am trying to play the DVD, it is shown as under.
"An error occurred. Could not open location; you might not have permission to open the file."
Why it happens? Is there anything wrong on my part?:confused:

---

### Post by garvinrick4 on 2011-03-19
Have you installed libdvdcss2
```

rick@rick-HP:~$ aptitude show libdvdcss2
Package: libdvdcss2                      
State: installed
Automatically installed: no
Version: 1.2.10-0.3medibuntu1
Priority: optional
Section: free/libs
Maintainer: Medibuntu Packaging Team <medibuntu-maintainers@lists.launchpad.net>
Uncompressed Size: 111 k
Depends: libc6 (>= 2.7)
Replaces: libdvdcss-dev (<= 0.0.3-3), libdvdcss0 (<= 1.0.0-0.0), libdvdcss2-dev
          (<= 1.2.10-0.0)
Provides: libdvdcss
Description: Simple foundation for reading DVDs - runtime libraries
 To allow applications to access some of the more advanced features of the DVD
 format.
Homepage: http://download.videolan.org/

```

---

### Post by Sofa_King_Cool79 on 2011-09-27
> **AnupamMitra said:**
> I placed the DVD in the player's window. Movie Player was installed earlier. When I am trying to play the DVD, it is shown as under.
"An error occurred. Could not open location; you might not have permission to open the file."
Why it happens? Is there anything wrong on my part?:confused:

Make sure you have libdvdread4 installed, you can check for this in synaptic package manager. 

Then all you have to do is run this command in terminal

```
sudo /usr/share/doc/libdvdread4/install-css.sh

```

I was getting the same exact error you were and this rectified the issue.

more info on that here: [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs]("https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs")

---

### Post by WasMeHere on 2011-09-27
> **AnupamMitra said:**
> I placed the DVD in the player's window. Movie Player was installed earlier. When I am trying to play the DVD, it is shown as under.
"An error occurred. Could not open location; you might not have permission to open the file."
Why it happens? Is there anything wrong on my part?:confused:

Try this thread: [_**[COLOR="Red"]Comprehensive Multimedia & Video Howto[/COLOR]**_]("http://ubuntuforums.org/showthread.php?t=766683")
It may take some time, but the result is very good, you will get a solid multimedia system.

---

