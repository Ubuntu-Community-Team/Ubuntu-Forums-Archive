---
title: "Zte mf636"
date: 2009-11-04
forum: Networking &amp; Wireless
---

### Post by Placidia on 2009-11-04
Has anyone got the ZTE MF636 mobile internet stick working on Koala? I had it working fine with Jaunty - using Rogers (Canada) service.

It didn't work when I installed Koala. The light went blue and lsusb recognized it. I set up a connection in network manager, but the icon did not appear to enable me to connect. 

I understand there is a bug in the network manager and a number of mobile sticks are affected. Is there a workaround?

I have re-installed Jaunty and everything is working fine again, but if/when the ZTE can work on Koala, I would like to know.

Thanks

---

### Post by superpal on 2009-11-04
well
 
the zte 636 modem do not work for me at all
i treid to do many configurations and commands but nothing
 
if u help me to install the Jaunty  to make it work 
 
ill be thankfull for u
 
thank u

---

### Post by Placidia on 2009-11-04
There are a number of postings on this site about the ZTE and Jaunty. I have to admit that I don't understand most of them.

This is what worked for me:

The trick with the ZTE as sold by Rogers Canada is that it is configured to make the computer think that it is an internal CD drive or something like that.  First, one needs to change the configuration. The easiest way is to insert the stick into a PC running Windows.  Do Control Panel -> Modem -> Dialing Properties. Use the Classic View. Under the tab for "init strings", put

AT+ZCDRUN=8

Then start the connection software. The system will connect, then drop the connection and give an error. This shows that the fix has worked.  The stick will no longer be usable with Windows. 

(Apparently, to return it to the original state, use init string:
AT+ZCDRUN=9


I have not done this, so don't know if it works.)

A certain amount of the advice on this forum to get a ZTE running consists of bash commands aimed at achieving the same result as above. So if there is a Windows box in your neighbourhood, use it.

Then, right click the connection manager on the top banner and choose "edit connections"

Create a new connection under the tab Mobile Broadband

With luck, your provider will be there. Choose your country and then your provider. If your provider is not there, you will need to find password and user info from that entity.

When the stick is plugged in, your provider will show up on the list of connections. Click and Go!

I should add that I had already used my stick with Windows before switching to Ubuntu, so the stick had been activated by the provider. I assume you have done that already.

---

### Post by superpal on 2009-11-05
Thank u for your reply but i tried to do the configuration u told me about in the PC but i faild in doing it. in the PC control panel I did not find modem i found phone and modem. even with this one i did not know how to do the configuration u told me about
plz help in more details.
 
 
thank u :)

---

### Post by Placidia on 2009-11-06
Yes, you're right. You want the icon for "phone and modem."

Using Windows XP:

Plug in the stick. Windows will "search for new hardware" and hopefully identify the ZTE. This could take a minute or two.

If you check under "modem" in "Phone and modem", your stick should show up.

Select the stick and click on Properties. I can't remember if "properties" shows up or if you need to right click and find a context menu.

Get into the properties tab and choose "Advanced."

Under "Advanced" there is an input box with a title like "initialization string" or "input initialization"  That's where you type AT+ZCDRUN=8

Next, you start the modem. The Rogers stick came with software that dialed you into the Rogers network. Launching that app started the modem and invoked the AT+etc command. If you don't have software like that on your stick, you will have to start the modem in some other way -- possibly by dialing a number.

As far as I can remember, that's what I did. I have not had to do it since then, because once the stick works, it keeps on working.

I should say that my stick only works as a modem. I can't use it as a USB storage device, which I could do on Windows.

Alternatively, you can work through the instructions given elsewhere on this forum for using modeswitch

---

### Post by superpal on 2009-11-08
thank you for your rely. i got it. but i can do it without the windpes by changing
19d2:2000 to 19d2:0031 by using the comand lsusb
 
by this command
 
sudo /usr/sbin/usb_modeswitch -W -c /etc/usb_modeswitch.conf
 
you can see what i did but unfortunately i faild to make it work. coz there could be some little mistakes
 
[http://ubuntuforums.org/showthread.php?t=1314270&highlight=zte](http://ubuntuforums.org/showthread.php?t=1314270&highlight=zte)
 
:)

---

