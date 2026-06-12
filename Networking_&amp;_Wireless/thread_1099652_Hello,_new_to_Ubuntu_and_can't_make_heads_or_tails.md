---
title: "Hello, new to Ubuntu and can't make heads or tails of this information."
date: 2009-03-18
forum: Networking &amp; Wireless
---

### Post by altfive on 2009-03-18
Alright, someone asked this question before, I didn't see an answer so decided to make my own thread. There are programs for both Mac and Windows, but Linux is not "officially" supported.

I have no idea what this means, or where I can possibly input this information. I can get to a "LPR/LPD" type option in System/Admin/Printing and then clicking on "new." From there I can't figure out what to do though. Can anyone help me out? Thanks! :)


add a new printer on your workstation with the following settings:

* Queue type: choose LPR/LPD/Networked Unix
* Server: [Server name]
* Server-side queue name: ePrint-OIT
* Workstation-side queue name: selected by user (OIT recommends ePrint-OIT)
* Printer type: Use HP LaserJet 4100dtn (or closest equivalent)

When you send print jobs from your personal Unix or Linux system, you need to include your NetID as a parameter to the lpr printing command &#8211; both from the GUI and from the command line. To do so, add the -U flag followed by your username.

For example, to print foo.txt from the command line on your Linux system, a user with the NetID of john would enter lpr -P ePrint-OIT -U john foo.txt.


EDIT::

Ok, I think I have the printer set up and I can print from the command line, I haven't yet tried it (in the middle of a class) but I can't get the next part figured out, at least in OpenOffice. Here is the info they give. Any info on this would be great :D


From a GUI/XWindows application, you will need to modify the print command. This is usually changed within the Print dialog box, often under the Properties button for the selected printer. Add -U followed by your NetID (as in the -U john example) to the print command.

---

