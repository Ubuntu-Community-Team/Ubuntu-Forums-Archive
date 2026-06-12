---
title: "Cannot send media keys with remote"
date: 2008-08-12
forum: Multimedia Software
---

### Post by humble_coffee on 2008-08-12
I'm trying to get my remote to control to have the same functionality as the media keys on my keyboard, but I'm having no luck at at all.

Here are the different ideas I've come up with:

1. Have the remote send a simulated key event using lirc and irxevent. 

This is normally done using the irxevent program, but unfortunately it seems like irxevent doesn't support the the media keys. Either that, or I didn't feed my .lircrc the right name of the key. eg: for the increase volume button, I entered the name of the key as 'XF86AudioRaiseVolume.

2. Have the remote control send the underlying command of the media keys.

I was hoping that there was some command that the media keys used to perform their actions, and if so, I could just target that command with lirc and irexec. But I'm beginning to suspect that maybe there is no command, the event is just handled in some code somewhere.

3. Use xbindkeys to remap a key combination to send a media key event, then Target the key combination with lirc and irxevent.

The problem with this one, is I don't know if xbindkeys can actually target another key event rather than a command.

Anyone have any other suggestions or know how to make one of these work??

---

### Post by humble_coffee on 2008-08-25
*bump*

arrg, I still haven't gotten anywhere with this. does anyone have any ideas??

---

### Post by jackflap on 2009-10-11
I was looking around for this as well.

You can either send map the media keys to buttons you can configure using irxevent (i.e. F10 for volume up). This can be done under System -> Preferences -> Keyboard Shortcuts. And then you configure irxevent to hit F10 on button press.

Or, another way I came across was using irexec. i.e. place the following in your .lircrc and running irexec should execute the command, and up your volume:

```
begin
    prog = irexec
    button = KEY_VOLUMEUP
    config = echo KeyStrPress XF86AudioRaiseVolume KeyStrRelease XF86AudioRaiseVolume | xmacroplay $DISPLAY
end

```

You might need to 'sudo apt-get install xmacro' to get xmacroplay to work.

---

### Post by reuben on 2010-02-24
I took a similar approach using xte, isntead of xmacro; see the last section here: [http://flavor8.com/index.php/2010/02/24/how-to-use-a-remote-control-to-control-banshee/#Control_Volume](http://flavor8.com/index.php/2010/02/24/how-to-use-a-remote-control-to-control-banshee/#Control_Volume)

---

