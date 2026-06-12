---
title: "Desktop Video Capture w/ Compiz"
date: 2009-09-16
forum: Multimedia Software
---

### Post by mikeym on 2009-09-16
Could someone point me in the direction of a desktop video capture that works with compiz?

---

### Post by mikeym on 2009-09-16
OK I found recordmydesktop worked well enough and made a little script for it:

Install recordmydesktop and zenity

```
sudo apt-get install recordmydesktop zenity
```

Download an [icon]("http://www.iconfinder.net/ajax/download/png/?id=18270&size=128") for it and then copy it to *.local/share/icons/video.png*

```
cp 1253105813_cam_unmount.png ~/.local/share/icons/video.png
```


Save the following file to desktopcapture
*desktopcapture*
```
#!/bin/bash
# Toggle desktop recording
if pgrep recordmydesktop; then 
	echo "killing zenity notification"
	kill `cat /tmp/desktopcapture` 2> /dev/null	
	echo "killing recordmydesktop"
	killall recordmydesktop
	FOLDER=`basename $HOME`
	echo "opening zenity dialogue"
	zenity --info --text="Video saving to <i>$FOLDER</i>..." --title="Desktop Capture" --width=250 --window-icon="$HOME/.local/share/icons/video.png" &
else 
	echo "starting recordmydesktop"
	recordmydesktop &
	echo "starting zenity notification"
	zenity --notification --text="Recording Desktop" --window-icon="$HOME/.local/share/icons/video.png"  &
	echo $! > /tmp/desktopcapture
fi

```

Then make executable and copy into path

```

chmod +x desktopcapture
sudo cp desktopcapture /usr/local/bin

```

Then bind a keyboad shortcut to it - in whichever way suits you best. (Metacity, Compiz or Keyboad Shortcuts.)

---

