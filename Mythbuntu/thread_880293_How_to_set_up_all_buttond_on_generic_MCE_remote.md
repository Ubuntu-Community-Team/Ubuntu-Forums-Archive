---
title: "How to set up all buttond on generic MCE remote?"
date: 2008-08-04
forum: Mythbuntu
---

### Post by bmwman on 2008-08-04
I just got this remote from Newegg : [http://www.newegg.com/Product/ShowImage.aspx?Image=80-121-003-03.jpg%2c80-121-003-04.jpg%2c80-121-003-05.jpg%2c80-121-003-06.jpg%2c80-121-003-07.jpg%2c80-121-003-08.jpg%2c80-121-003-02.jpg&S7ImageFlag=0&WaterMark=1&Item=N82E16880121003&Depa=0&Description=Anyware+GP-IR01BK+Infrared+Windows+Vista+MCE+Black+Remote+Control](http://www.newegg.com/Product/ShowImage.aspx?Image=80-121-003-03.jpg%2c80-121-003-04.jpg%2c80-121-003-05.jpg%2c80-121-003-06.jpg%2c80-121-003-07.jpg%2c80-121-003-08.jpg%2c80-121-003-02.jpg&S7ImageFlag=0&WaterMark=1&Item=N82E16880121003&Depa=0&Description=Anyware+GP-IR01BK+Infrared+Windows+Vista+MCE+Black+Remote+Control)

I really like and it has all the buttons that I need. It works out of the box with the Window Media Center remotes(new Phillips) setting. The main buttons work, but not all tho. I want to make the Home, Guide, Recordings, LiveTV and whole bunch of other ones work as well. I tried to find some How-To online but everything seems so confusing to me. How do you set the codes for each button and how do you get a list of the available buttons? Then how do you make each button to do what you want it to do?

Where should I start?

Thanks

---

### Post by bmwman on 2008-08-04
Ok I just found out about IRW and got the codes from the buttons. They looke like that:
000000037ff07bb6 00 Pictures mceusb
000000037ff07bb6 01 Pictures mceusb
000000037ff07bb6 02 Pictures mceusb
000000037ff07bb5 00 Videos mceusb
000000037ff07bb5 01 Videos mceusb
000000037ff07bb5 02 Videos mceusb
000000037ff07bb7 00 RecTV mceusb
000000037ff07bb7 01 RecTV mceusb
000000037ff07bd9 00 Guide mceusb
000000037ff07bd9 01 Guide mceusb
000000037ff07bda 00 LiveTV mceusb
000000037ff07bda 01 LiveTV mceusb
000000037ff07bda 02 LiveTV mceusb
000000037ff07bdb 00 DVD mceusb
000000037ff07bdb 01 DVD mceusb
000000037ff07bdb 02 DVD mceusb
000000037ff07be8 00 Record mceusb
000000037ff07be8 01 Record mceusb
000000037ff07be8 02 Record mceusb
000000037ff07bdc 00 Back mceusb
000000037ff07bdc 01 Back mceusb
000000037ff07bf2 00 Home mceusb
000000037ff07bf2 01 Home mceusb
000000037ff07bf2 02 Home mceusb
000000037ff07bf5 00 Clear mceusb
000000037ff07bf5 01 Clear mceusb
000000037ff07bf5 02 Clear mceusb
000000037ff07bf4 00 Enter mceusb
000000037ff07bf4 01 Enter mceusb
000000037ff07bf4 02 Enter mceusb
000000037ff07ba5 00 Teletext mceusb
000000037ff07ba4 00 Red mceusb
000000037ff07ba4 01 Red mceusb
000000037ff07ba3 00 Green mceusb
000000037ff07ba3 01 Green mceusb
000000037ff07ba3 02 Green mceusb
000000037ff07ba2 00 Yellow mceusb
000000037ff07ba2 01 Yellow mceusb
000000037ff07ba2 02 Yellow mceusb
000000037ff07ba1 00 Blue mceusb
000000037ff07ba1 01 Blue mceusb
000000037ff07ba1 02 Blue mceusb
000000037ff07bf3 00 Power mceusb
000000037ff07bf3 01 Power mceusb
000000037ff07bf3 02 Power mceusb

So what do I do now? And why there are multiple lines for each button, like what does 00,01 and 02 means?

Thanks

---

### Post by bah1976 on 2008-08-05
The multiple lines have to do with the repeat - if you hold the button down longer you'll get more lines.  

This is a good place to start:
[http://www.mythtv.org/wiki/index.php/MCE_Remote#Example_lircrc_config_file]("http://www.mythtv.org/wiki/index.php/MCE_Remote#Example_lircrc_config_file")

And I'll add my own notes too - For the specific buttons you mentioned, I have this config (I don't have the exact remote, so I left a few off - but this should give you an idea)

This is a portion of my ~/.lirc/mythtv file

```
begin
    remote = mceusb
    prog = mythtv
    button = Record
    config = R
    repeat = 0
    delay = 0
end
begin
    remote = mceusb
    prog = mythtv
    button = More
    config = I
    repeat = 0
    delay = 0
end
begin
    remote = mceusb
    prog = mythtv
    button = OK
    config = Return
    repeat = 0
    delay = 0
end
begin
    remote = mceusb
    prog = mythtv
    button = Home
    config = M
    repeat = 0
    delay = 0
end
begin
    remote = mceusb
    prog = mythtv
    button = RecTV
    config = Ctrl+O
    repeat = 0
    delay = 0
end
begin
    remote = mceusb
    prog = mythtv
    button = Guide
    config = S
    repeat = 0
    delay = 0
end
begin
    remote = mceusb
    prog = mythtv
    button = LiveTV
    config = Ctrl+L
    repeat = 0
    delay = 0
end
begin
    remote = mceusb
    prog = mythtv
    button = DVD
    config = Ctrl+V
    repeat = 0
    delay = 0
end
begin
    remote = mceusb
    prog = mythtv
    button = Clear
    config = D
    repeat = 0
    delay = 0
end
```

The basic setup is 
button=(what IRW says) and 
config=(what you want it to do)

Some of the configs are just finding the key that you want it to be, and using it that way, but some of the configs are not native.  I have LiveTV, RecTV and DVD set to jumpoints, which are hotkey combination kind of deals that when I press on the keyboard, go to that location in myth.  If you still have a keyboard connected, you can setup the key combinations in the frontend setup - (default layout is Utilities / Edit Keys) and find the jump points section.  I have "Watch Recordings" set to Control-O.  That corresponds with what I have my RecTV button programmed to "Ctrl-O"
While you're in the key mapping setup, find the commands for what you want the other buttons to do.  The command will be in the box at the bottom of the screen.  Take that, and put it in your ~/.lirc/mythtv file.
Kind of make sense?  If you get stuck, let me know.

---

### Post by bmwman on 2008-08-05
I tried doing that last night but it didn't do anything. I set up the jump points and couple of other buttons, none of them worked. Maybe I need to restart the Lirc. It was  getting very late so I went to bed. I'll try it tonight and let you know. Seems kinda simple after finding what's the name on the buttons.

Thanks for the response and let you know what happens later.
;)

---

### Post by bah1976 on 2008-08-05
I think you have to restart the frontend to re-read the mythtv config file.  If I remember right - that's what worked for me.

---

