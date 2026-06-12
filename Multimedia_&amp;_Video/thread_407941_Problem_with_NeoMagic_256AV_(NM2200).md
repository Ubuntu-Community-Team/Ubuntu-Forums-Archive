---
title: "Problem with NeoMagic 256AV (NM2200)"
date: 2007-04-12
forum: Multimedia &amp; Video
---

### Post by petroskhan on 2007-04-12
First off, if this problem has been addressed elsewhere, I apologize, but I couldn't find it.

I recently acquired a Toshiba Tecra 8000, with a PII 366 MHz, 128MB of RAM, and an 8GB HD.  Since it's such a cute little machine, I decided to throw Edubuntu on it for my 5 year old daughter.  Everything is great, it's working fine, but the resolution is 640x480.  Anyone remember what THAT looks like?  Anyway, that's the only resolution it will allow, under System > Prefernces > Screen Resolution.  When I check the etc/x11/xorg.conf file, it shows a resolution of 700x(something)  I forgot, and the 640x480.  Now, under windows, after loading the driver, I was able to get a resolution of 1024x768, which was quite nice, so I know the card is capable of more than what I am now getting.  Anyone have any ideas on this one?  I would be happy with 800x600 at this point, but I don't understand two things.  Why is not making available a resolution that is in the xorg.conf file, and why can't I get anything higher?  Any help for this dumb noob would be appreciated greatly.

---

### Post by physx on 2007-04-12
It sounds like you may want to change your color depth.  I just did this on my old laptop because the screen refresh rate was so slow, but if the depth is set too high, it could also cause problems with resolution like you're seeing.  This site (referred to in a previous post):

[http://othello.alma.edu/~07tmhopk/ubuntuhowto.html#resolution]("http://othello.alma.edu/~07tmhopk/ubuntuhowto.html#resolution")

Gives some information about making changes to the xorg.conf file, where you can change the settings for resolution and color depth.  You may be set for 24 bit, and want to move to 16.

(BTW, I got the link above from a post titled "Help!! lost high resolution" which might also be helpful)

Hope this helps, but let us know what you see after trying out some changes.

---

### Post by petroskhan on 2007-04-12
Well, I have tried to modify the xorg.conf file, adding the resolution 1024x768, but still, when I go to the Screen Resolution settings, it will not let me select any resolution that is in the xorg.conf file.  It is set to 640x480, and will not let me select anything else.  I don't get it.  I also have that black border along the right side, and a smaller one along the bottom.  Under Windblows, I was getting really good resolution on this old computer, and now, on a MUCH better OS, I can't get even a usable resolution...can I get a tissue?  I may cry here....sniff....

Is there a section of the xorg.conf file that tells the computer to default to a certain resolution, or...I don't know.  I'm so new to this I don't even know what questions to ask.  Embarassing, that's what this is.

---

### Post by physx on 2007-04-14
I looked around the web, and found [this page]("http://outlands.ca/linux/t8000.html") that might be helpful (it specifically mentions the resolution problem).  It makes it sound like the frequency settings may be the problem, and that you'd want to change those settings to the following:

        HorizSync       36-52
        VertRefresh     36-60

Also, [here]("https://launchpad.net/ubuntu/+source/xorg/+bug/25079") is a bug report that is mentioned in the page above that follows the history for this specific one.  It seems like the fix above worked for several folks.

Hope this helps, but keep checking back in either way!

---

### Post by petroskhan on 2007-04-17
Well, it was a combination of things.  Problem is fixed now.  I had configured the xorg.conf file correctly, but had failed to execute the command (I've forgotten what it is now) to have the system reload the file.  Once it was reloaded, everything worked fine, so problem is now solved.  Thanks for the all the help on this issue.  My daughter is loving her new computer now.  :D

---

### Post by physx on 2007-04-17
Glad to hear that you were able to fix it, although I don't know if I did much to help.  Hope that your daughter enjoys it!

---

### Post by phewbuntu on 2008-03-26
Wow, thanks Physx.
I have an HP OmniBook 4150.  After an hour searching I found this post with your solution.  My monitor looked just fine while booting up and shutting down.  In between, however, the chocolaty, creamy, coffee colors of Ubuntu were oddly purple.  The colors for almost everything were off.  I altered the xorg.conf file setting the color depth to 16 bits and adjusting the vertical and horizontal rates to what you suggested and upon reboot.  Everything looked great.  Thanks.

---

