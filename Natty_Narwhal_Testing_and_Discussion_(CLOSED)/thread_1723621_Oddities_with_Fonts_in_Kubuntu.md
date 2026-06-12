---
title: "Oddities with Fonts in Kubuntu"
date: 2011-04-07
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by jlacroix on 2011-04-07
I noticed some strange things with the fonts in Kubuntu, and I wonder if I should file a bug report. 

I changed the font settings in System Settings to use anti-aliasing enabled, and force fonts dpi to 96. (Learned behavior from previous versions of KDE).

Here's where things get weird. I logged out and logged in, and wasn't really happy with the way things looked, so I set the settings back to the way they were before. (Use anti-aliasing: system settings, and force fonts DIP to disabled). After logging out and logging in, and even rebooting, the fonts did not return back to normal like they were when Kubuntu was first installed. In fact, logging out and deleting the .kde folder and .kderc files also won't turn the settings back.

Also, if I click on "defaults" on the font settings, all the fonts change from the Ubuntu font to the sans serif font. I would've thought the defaults on this would have been changed to the Kubuntu defaults in the code or something.

Is this a bug?

---

### Post by VMC on 2011-04-07
Interestingly, I also check the same anti-aliasing yesterday. I didn't change the dpi, but it appears to look better, but not near as good as Ubuntu fonts. I tried to match them up, but still a no-go. I think its a KDE issue.

I've googled around and found someone trying this several years ago, but the KDE fonts are for chrome use are horrible.

---

### Post by jlacroix on 2011-04-07
> **VMC said:**
> Interestingly, I also check the same anti-aliasing yesterday. I didn't change the dpi, but it appears to look better, but not near as good as Ubuntu fonts. I tried to match them up, but still a no-go. I think its a KDE issue.

I've googled around and found someone trying this several years ago, but the KDE fonts are for chrome use are horrible.
That may be, but I haven't had problems like this outside of Kubuntu. I mainly use Arch and their fonts seem to work better, so I assume that this may have to do with hacking KDE to use Ubuntu's fonts, and missing something in the process. Then again, I am not sure. :(

---

### Post by ft_ on 2011-04-07
[https://bugs.launchpad.net/ubuntu-font-family/+bug/744812](https://bugs.launchpad.net/ubuntu-font-family/+bug/744812)

---

### Post by jlacroix on 2011-04-07
> **ft_ said:**
> [https://bugs.launchpad.net/ubuntu-font-family/+bug/744812](https://bugs.launchpad.net/ubuntu-font-family/+bug/744812)
Thanks, now that I know it's already reported I'll just stand by and see if an update fixes it.

---

