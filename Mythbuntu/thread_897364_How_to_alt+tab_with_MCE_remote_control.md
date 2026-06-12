---
title: "How to alt+tab with MCE remote control ?"
date: 2008-08-22
forum: Mythbuntu
---

### Post by lizzer on 2008-08-22
I've been googling around now for awhile but I cannot find any useful page to this problem.

I'd like to be able to switch between mythtv and xbmc (alt+tab I guess..) with my MCE remote control. But how.. :confused:

Remote control works fine with both xbmc and mythtv. I know lirc is a key word, but I just can't get my head around it. 

I think I should do something like this on my .lircrc -file

```

begin
    remote = mceusb
    prog = mythtv
    button = red
    config = Alt+Tab
    repeat = 0
    delay = 0
end

```

This however does not work. I guess "prog" should be something else than mythtv ? And is the syntax Alt+Tab correct ?

Any help appreciated! :)

---

### Post by lizzer on 2008-08-22
Oh well.. I guess it is impossible. :cry:

---

### Post by KillerKiwi on 2008-08-24
you need a irexec app running in the background to capture the event and send a fake xkeys signal

---

### Post by OlegVekhov on 2010-04-29
I've wrote a simple script to do this trick! You may try it if you wish:

You need to have lirc configured and installed. You need irexec running in the background.

Also you need the *xmacro* package.

create file named /opt/alttab with following content:

```

#!/bin/bash
if [ -e /var/tmp/alttabtrig1 ]
 	then
		echo -e "KeyStr Tab"|xmacroplay ":0.0"
		touch /var/tmp/alttabtrig2
		exit
fi
if [ ! -e /var/tmp/alttabtrig1 ]
	then
		echo -e "KeyStrPress Alt_L\n
		KeyStr Tab"|xmacroplay ":0.0"
		touch /var/tmp/alttabtrig1
		touch /var/tmo/alttabtrig2
		while [ -e /var/tmp/alttabtrig2 ]; do
			rm /var/tmp/alttabtrig2
			sleep 2
		done
		echo -e "KeyStrRelease Alt_L"|xmacroplay ":0.0"
                rm /var/tmp/alttabtrig1
fi
```

sudo chmod a+x /opt/alttab

Then add this to your ~/.lircrc

```
begin
	prog = irexec
	remote = mceusb
	button = play
	config = /opt/alttab &
	repeat = 0
	delay = 0
end
```

Note the path to your file, the remote parameter and the button parameter may vary depending on your needs.

---

