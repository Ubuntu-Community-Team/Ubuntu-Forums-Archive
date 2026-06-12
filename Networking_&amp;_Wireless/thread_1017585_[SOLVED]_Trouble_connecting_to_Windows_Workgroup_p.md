---
title: "[SOLVED] Trouble connecting to Windows Workgroup printer"
date: 2008-12-21
forum: Networking &amp; Wireless
---

### Post by ggb-uk on 2008-12-21
[LEFT][COLOR=black]xLde>en Googlec[IMG]http://ubuntuforums.org/data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAABwAAAAOCAYAAAA8E3wEAAAABmJLR0QA/wD/AP+gvaeTAAAACXBIWXMAAAsTAAALEwEAmpwYAAAAB3RJTUUH1QUUDyoqJjAqRwAAAN1JREFUOMu1lMkVwyAMBYe0JGpCNUFNVk3k4AUwxPGS+ILxkzX8jyTH/Sfu9nrmJ3cXlnMASyWRPwd2d5XlHCBZn1BthcbRAdxTZQDI8k3mQzg11rhF+QZ9jdNOcQib6GFQYJYgCFucSRf6GsLU6wEY5yubTFqF2yq1vRwr3INXdQUWG+je1pELX4ED1wDyRAR0WfuAA9gloITyvsFMIMgYInYRqF6rO9Sqz9qkO5ilyo0o3YBwJ+6vrdQonxWUQllhXeHcb/wabMPkP2n81ocAIoLZrMqn/4y2RwP8DcQ+d6rT9ATiAAAAAElFTkSuQmCC[/IMG]
[/COLOR][/LEFT]
I have just installed Ubuntu AMD64, and am still trying to get everything connected up.

I have a Canon MP510 printer/scanner attached to a Windows XP that I would like to share with my Ubuntu workstation.

I can see the printer share on another computer running Windows 2000.

I can see the Windows XP computer (the one with the printer share) when I go to Places/Network - and I can see from there all the file shares that are being shared by the XP.  I cannot see the printers being shared here, but that may be normal, since the application is a file browser and not a printer browser.

When I start up the printers application, that would allow to to set up new printers, and I select 'New Printer', and than ask to browse Windows printer shares, I can see another Linux computer (set up with Debian) running Samba, but not only can I not see the Windows XP printer being shared, but the computer itself is not visible from this application.

How then can I go about connecting to the Windows printer from Ubuntu?

Incidentally, I have downloaded the Canon drivers for the printer onto Ubuntu - although I had to tweek the drivers, as they only downloaded with i386 and not amd64, so I had to unpack the package, change the package to say it was running under amd64, and repackage and install it.  I have yet to prove that this tweek will work, but as at present I cannot even connect to the printer, I am in no position to test if the driver for the printer is configured correctly.

---

### Post by superprash2003 on 2008-12-21
while clicking on "new printer" .. select connect via samba .. and insert the whole link of th eprinter location like x.x.x.x/printername where x.x.x.x is the ip of the xp machine..

---

### Post by ggb-uk on 2008-12-21
[LEFT][COLOR=black]xLde>en Googlec[IMG]http://ubuntuforums.org/data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAABwAAAAOCAYAAAA8E3wEAAAABmJLR0QA/wD/AP+gvaeTAAAACXBIWXMAAAsTAAALEwEAmpwYAAAAB3RJTUUH1QUUDyoqJjAqRwAAAN1JREFUOMu1lMkVwyAMBYe0JGpCNUFNVk3k4AUwxPGS+ILxkzX8jyTH/Sfu9nrmJ3cXlnMASyWRPwd2d5XlHCBZn1BthcbRAdxTZQDI8k3mQzg11rhF+QZ9jdNOcQib6GFQYJYgCFucSRf6GsLU6wEY5yubTFqF2yq1vRwr3INXdQUWG+je1pELX4ED1wDyRAR0WfuAA9gloITyvsFMIMgYInYRqF6rO9Sqz9qkO5ilyo0o3YBwJ+6vrdQonxWUQllhXeHcb/wabMPkP2n81ocAIoLZrMqn/4y2RwP8DcQ+d6rT9ATiAAAAAElFTkSuQmCC[/IMG]
[/COLOR][/LEFT]
superprash2003,

Thanks for your reply.

OK, that has substantially fixed my problem.

The kludged MP510 driver does not work, but if I set it up using the PIXMIA iP4000 driver, I can get the test page printing.  I am not sure if this is the ideal driver, but the PIXMIA iP3000 does not work - so if anybody can let me know what the ideal driver is for the MP510 I would be grateful - but at least I am now getting some output.

Thanks.

---

### Post by ggb-uk on 2008-12-21
[LEFT][COLOR=black]xLde>en Googlec[IMG]http://ubuntuforums.org/data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAABwAAAAOCAYAAAA8E3wEAAAABmJLR0QA/wD/AP+gvaeTAAAACXBIWXMAAAsTAAALEwEAmpwYAAAAB3RJTUUH1QUUDyoqJjAqRwAAAN1JREFUOMu1lMkVwyAMBYe0JGpCNUFNVk3k4AUwxPGS+ILxkzX8jyTH/Sfu9nrmJ3cXlnMASyWRPwd2d5XlHCBZn1BthcbRAdxTZQDI8k3mQzg11rhF+QZ9jdNOcQib6GFQYJYgCFucSRf6GsLU6wEY5yubTFqF2yq1vRwr3INXdQUWG+je1pELX4ED1wDyRAR0WfuAA9gloITyvsFMIMgYInYRqF6rO9Sqz9qkO5ilyo0o3YBwJ+6vrdQonxWUQllhXeHcb/wabMPkP2n81ocAIoLZrMqn/4y2RwP8DcQ+d6rT9ATiAAAAAElFTkSuQmCC[/IMG]
[/COLOR][/LEFT]
OK, I did see there was a driver for the MP520, and that seems to work fine (and looking at the output from that driver it is clear that the printed output from the iP4000 driver was in error).

E verything now printing OK.

Thanks again.

---

