---
title: "Enable and connect mobile broadband from command line script?"
date: 2010-07-27
forum: Networking &amp; Wireless
---

### Post by quinthar on 2010-07-27
I have a Sony TZ270N running Ubuntu 10.04 splendidly.  The Sprint Mobile Broadband works great, but it's a bit cumbersome to activate.  Specifically, to get it to work I need to:

echo 0 > /sys/devices/platform/sony-laptop/wwanpower
sleep 5
echo 1 > /sys/devices/platform/sony-laptop/wwanpower

Then I wait another five seconds, right-click on the networking icon, choose "Enable mobile broadband", then left-click on the networking icon, and choose "Connect to Sprint Connection".  I do this multiple times a day, and it's just a bit of a pain, especially when in a hurry.  Accordingly, I'd like to script it so I can do the whole thing with a single command.

I've already put the above echo statements into a script and it works great; is there any way to script the actual start of the PPP session itself -- with the caveat that I'd like the networking icon to accurately reflect the latest state?

(In other words, I don't want to bypass the networking icon and just launch the PPP session in the background -- I want it to show that I'm connected, and still let me manage the connection via the icon after connected.)

Is such a thing possible?  Thanks, I really appreciate your advice!

-david

---

### Post by alexfish on 2010-07-27
[http://wireless.kernel.org/en/users/Documentation/NetworkManager](http://wireless.kernel.org/en/users/Documentation/NetworkManager)

---

### Post by quinthar on 2010-07-27
Thanks for the link, but I don't see anything in the documentation that indicates how to do this.  Searching around a bit more I see that it might be configurable via dbus (but I'm not really sure what that means), and that there might be some application called nmcli (but it doesn't seem to be installed and I can't apt-get it).  I also see a NetworkManager application, but the manpage makes it seem like that's more of a background daemon (at least, it doesn't seem to offer the parameters I need).  I apologize for my confusion, can you point me to a reference of some easy way to script the network manager via the command line?

For example, is there some command where I can say:

```
nmcli enable wwan
nmcli connect wwan
```

Or, is there some easy command I can run through this mythical dbus, like:

```
dbus-send NetworkManager enable wwan
dbus-send NetworkManager connect wwan
```

I see some documentation here [(link)]("http://projects.gnome.org/NetworkManager/developers/spec.html#org.freedesktop.NetworkManager.Connection.Active") but I'm not up to speed on it (and I'm not sure if I'm barking up the wrong tree).

Thanks, I really appreciate your help!

-david

---

### Post by leonbravo on 2011-04-15
I have that doubt today.

So far, I couldn't find a precise solution.... but here some light to your ideas.


nmcli -p dev list # will show you all available connections.

you can bring down your mobile broadband with

nmcli con down id yuorbroadband # my case Movistar

If you are guessing changing down for up will do it ... .nah, it doesn't. I don't know why.


Then you can try. lsusb to see your usb stick and then, 

 usb_modeswitch -H -p 1446 -v 12d1 -W  

What excactly does that, don't ask me .....

if you find out more, please update the thread.

---

### Post by ffaxer on 2011-12-24
From reading the man page of nmcli i found these commands to be equivalent of clicking 'Enable Mobile Broadband'

```

nmcli nm wwan on
nmcli nm wwan off

```

I know its an old thread but it still comes up in searches for this problem, so..

If you set your specific broadband connection to connect automatically (Edit connections->Mobile Broadband), it should try to connect as soon as you succesfully enable wwan.

If not, try

```

nmcli con up id "Name Of Your Connection"

```

nmcli seems very solid for scripting Network Manager. I've used wvdial in the past, but now I would only resort to that if Network Manager does not work for a connection.

Lastly, and a bit offtopic, if you feel lonely one day and want to talk to your modem(!), I just found out you can do it without minicom or that type of serial communication tool. You can pipe stuff directly from the echo command to the modem device, start by opening a terminal for the modem responses:

```
cat /dev/ttyACM0
```

Leave it open and now open another terminal to send commands like this:

```

echo -e "at\r\n" > /dev/ttyACM0

```

You should be able to see responses from the modem like "OK" or whatever in the first window. Pretty cool me thinks!

I have been trying to do that before without luck, but I found that my modem expects a CR (\r) character at the end of a line, and the usual newline (\n) won't work. In the example though, I send both just to be sure.

Notice the -e option which allows escaped characters such as \r. on other systems this is default, and so not needed, or perhaps the option is named something else on your system, in which case RTFM..

Also note that the particular device file for your modem will likely be something else than /dev/ttyACM0, I leave it to you to find that out.

If you need "conversational topics" do a search for "Hayes commands" :D

Also, M e r r y X M a s!

---

