---
title: "Touchscreen on Lenovo X200 ThinkPad"
date: 2013-11-22
forum: Multimedia Software
---

### Post by jord1981 on 2013-11-22
I just installed Lubuntu 13.10.  I've installed the wacom drivers but have no response from touchscreen.

Any tips?

Thanks so much in advance.

---

### Post by Favux on 2013-11-23
Hi jord1981,

It should have worked out of the box without a need to install drivers.  What exactly did you do?

Let's check if the Wacom usb kernel driver/module is auto-loading:
```
lsmod | grep wacom
```
When did Lenovo go from the serial connection to the usb one?  The X200t or the X220t.  Talking to myself, have to look that up if it doesn't come to me.

Let's see if it is on the Wacom X driver:
```
xinput list
and 
xsetwacom list
```
Check your version of xf86-input-wacom:
```
xsetwacom -V
```
Ubuntu calls it the xserver-xorg-input-wacom package.

---

### Post by jord1981 on 2013-11-23
Hi Favux,

I installed from CD, didn't work.  Went to package manager and installed wacom, didn't work.  Then I came here.

Here are the results of the commands you suggested:

lsmod | grep wacom -> returned nothing

xinput list:> 
&#9121; Virtual core pointer                          id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                id=4    [slave  pointer  (2)]
&#9116;   &#8627; TPPS/2 IBM TrackPoint                     id=11   [slave  pointer  (2)]
&#9116;   &#8627; Serial Wacom Tablet stylus                id=13   [slave  pointer  (2)]
&#9116;   &#8627; Serial Wacom Tablet eraser                id=14   [slave  pointer  (2)]
&#9123; Virtual core keyboard                         id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard               id=5    [slave  keyboard (3)]
    &#8627; Power Button                              id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                 id=7    [slave  keyboard (3)]
    &#8627; Sleep Button                              id=8    [slave  keyboard (3)]
    &#8627; UVC Camera (17ef:480c)                    id=9    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard              id=10   [slave  keyboard (3)]
    &#8627; ThinkPad Extra Buttons                    id=12   [slave  keyboard (3)]

xsetwacom list:
> Serial Wacom Tablet stylus              id: 13  type: STYLUS    
Serial Wacom Tablet eraser              id: 14  type: ERASER    

xsetwacom -V: 0.20.0

---

### Post by jord1981 on 2013-11-23
x

---

### Post by Favux on 2013-11-23
OK, **xinput list** shows us it is still a serial connection.  So the usb kernel driver wacom.ko isn't needed and **lsmod** returning nothing is normal.

Further **xinput list** shows the digitizer is on the Wacom X driver.  The Wacom X driver (xf86-input-wacom) is what is appending stylus and eraser to the Parent Device name of "Serial Wacom Tablet".  And **xsetwacom list** confirms that because if it wasn't on the Wacom X driver it would have returned nothing.

From what we have right now it appears the driver is installed and the digitizer/stylus should be working.  That suggests a hardware problem.  Most likely the stylus.  The Wacom pen is active, i.e. has an electromechanical broadcast from an antenna, and can break.  Do you have spare stylus you can test with or can you borrow one?  Does the stylus work if you are on another Ubuntu release or linux Distro?  Does it work in Windows?  A replacement stylus is not very expensive.

---

### Post by jord1981 on 2013-11-24
Thanks for your help.  Replaced stylus and it works.  However, I can't use my finger on the screen and can't use the stylus for text recognition.  Is there a driver for the former and an app for the latter?

---

### Post by Favux on 2013-11-24
Good.

Touch driver for a Wacom touch screen is xf86-input-wacom.  Are you sure you have a touch screen?  I think that was optional on a X200t.  It should have shown up in the xinput list as:
```
&#9116; &#8627; Serial Wacom Tablet touch id=? [slave pointer (2)]
```

Although there are several OSS ocr projects for some reason there isn't an OSS app. for handwriting recognition that I know of.  I've been expecting one to show up for a while.  Evernote had a demo a few years ago and there is a workaround using a Windows recognition engine.  CellWriter does give letter recognition.  That plus Xournal is a reasonable combination.

---

### Post by jord1981 on 2013-11-24
Thanks againI wrote this rep|y in cell writer. I`m not sure I understand how to integrate this with Xournal?

I think you're right that this is not a touchscreen.

---

### Post by Favux on 2013-11-24
I meant between the two of them you can accomplish a fair number of tasks, not that they can be integrated.

With CellWriter you can type/enter text either in its keyboard mode or character recognition mode.  Xournal you can take handwritten notes and annotate PDFs.  And so on.  But it's not OneNote, and what I want is a OneNote equivalent and I suspect you do too.  Maybe without quite all the bells and whistles.

---

### Post by jord1981 on 2013-11-25
I gotcha. I've been having a lot of luck with CellWriter the past 24 hours. Thanks so much for help!

---

### Post by lhs2miler on 2013-12-30
I have the X200 Tablet Touch version, and my touch shows up in the xinput list, but my touch screen coordinates are incorrect and I can't get them to work correctly.  I basically have the border 1 inch "untouchable."  I tried typing:
 sudo xsetwacom set "Serial Wacom Tablet touch" Area 48 90 915 940
But Ubuntu 13.10 fails to find/recognize the xsetwacom command.

Forgive me for my naivete, just hoping to get everything to work on the tablet....


Thanks!

---

### Post by jord1981 on 2014-01-23
Hey lhs2miler - I don't know how to fix your issue but people who do may not be looking at this old thread because it is marked solved.  You may want to try making a new thread.

---

