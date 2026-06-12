---
title: "42&quot; LCD wont detect proper resolution. How can i add a custom??"
date: 2009-02-01
forum: Multimedia Software
---

### Post by jastonas on 2009-02-01
I am using ubuntu 8.10 and have a 42" Samsung hdtv ready. The best resolution i can get is 1024x768 which even though is 4:3 it is better because it stretches whereas the next bigger resolution available 1360x768 is cutting parts of my screen out.

I ve benn looking for hours and i cant seem to find a way to add some custom resolutions and start trying. I am support the TV supports better resolutions than the current. 
I am using nvidia restricted 177 drivers.

---

### Post by jastonas on 2009-04-01
Sorry fro bringing this up but after so long not only have i not managed to find a solution, now i have the same problem with another screen. I have dual monitors same brank/make/model and one gets proper resolution but the one used as my second in twin view doesnt!

No easy way to add a custom resolution?

---

### Post by sagasha on 2009-04-01
I see you did not get a reply. Same thing when I posted a reply for help on the same topic a few weeks back.

It gets fruastrating when I suggest Ubuntu (or any Linux Distro) to friends and it's always the same question, "Why can't I choose a different resolution?"

I have a 16x10 screen aspect ratio ViewSonic but I can only pick 1440x900 in that ratio ( which for me is abit too small) and alot of 4x3 and 5x4 ratios. In Vista I have more options (1280x800 for example.) Why can't this be addressed?

---

### Post by aeiah on 2009-04-01
so let me get this straight, ubuntu runs the monitor in it's native resolution, but you want to use one with less pixels? why?

and although the monitor plays a small part, its mostly down to your graphics card and drivers. 

if you want to have weird resolutions then try aquiring the custom modelines from windows. pstrip allows this. then you can import them into your xorg.conf

---

### Post by sagasha on 2009-04-01
aeiah,

        What is wierd about wanting a different resolution? 1440x900 is 16x10 and so is 1280x800. I like the larger text, etc. It's nice to have options.

---

### Post by jastonas on 2009-04-02
> **aeiah said:**
> so let me get this straight, ubuntu runs the monitor in it's native resolution, but you want to use one with less pixels? why?


With the 42" Lcd, ubuntu would get only 4:3 resolutions for some reason while the screen was 16:10.
Now with my dual screen setup, as i said before, they are two same screens, the primary gets proper resolution the second one doesnt even have that option! For some reason ubuntu cant handle secondary screens. 2 times i tries both i ve had bad results.

---

### Post by sagasha on 2009-04-02
This thread will answer your question I think.
[Click here]("http://ubuntuforums.org/showthread.php?p=7002474#post7002474")

---

### Post by iheartubuntu on 2009-04-04
I agree it would be nice to have more resolution options. My dad (75 yrs old) for example likes bigger everything because his eyes get tired fast. It seems this is such a basic thing too.

---

### Post by ubu-for on 2009-04-04
Read the following HOWTOs.

[http://ubuntuforums.org/showthread.php?t=23628](http://ubuntuforums.org/showthread.php?t=23628)
[http://ubuntuforums.org/showthread.php?t=98456](http://ubuntuforums.org/showthread.php?t=98456)

---

### Post by stratus75 on 2009-04-04
Hi Guys 
have'nt found a solution to this problem myself yet either,(Ubu-for thanks for the howto's havent read them yet though thats my next step)
but would like to give my 2cents.
i have a Samsung 32" HDMI tv screen and have been having the same problems. 
what i reckon the problem is on my screen any way is, that there are 4 seperate inputs availible onthe this tv - HDMI, Ext1, Ext2 and vga(P.C imput) the later having [[COLOR="Blue"]EDID[/COLOR]]("http://en.wikipedia.org/wiki/Extended_display_identification_data") availible for the P.C to probe on that connection, but as i have the HDMI connection as my primary screen and the VGA as my secondary sceen (N.B these screens are different imputes on the same HDMI tv that i can switch between)
on a Nvidia 9600 gtx card using 180.44 driver from Nvidia, when Nvidia config probes the screen for resolutions on HDMI connection it gets the EDID information that is mention for the VGA connection and because the native resolution on VGA is'nt support on the HDMI screen, so the when Ubuntu loads i get the Ubuntu screen with the status bar and when it loads the desktop(i assume this is Xorg loading?) the HDMI screen just says mode unsupported (as in resolution not supported by TV in HDMI screen)
Hope this helps somebody.

---

### Post by Makiavelico on 2010-12-23
to fix resolution problems go here: [http://ubuntuforums.org/showthread.php?p=10271659#post10271659](http://ubuntuforums.org/showthread.php?p=10271659#post10271659)

You can find out how to make a custom resolution for your LCD.

---

