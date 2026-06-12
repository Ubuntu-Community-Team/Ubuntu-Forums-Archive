---
title: "Printer question"
date: 2010-02-11
forum: Networking &amp; Wireless
---

### Post by kbozz71 on 2010-02-11
Hi everyone, I have a desktop with Ubuntu 9.10 hosting an HP Deskjet 2460 printer. I want my wife's laptop to be able to print to it. The laptop is running Windoze XP Pro. Is there a "how to" someone can point me to? I've searched, but most similar problems that come up are much more involved. All I need is for that windows laptop to be able to print. Thanks. BTW,I have sharing/publishing enabled, and can see the printer from the internet(connecting to the 631 port) Thanks again.

---

### Post by johnson.d on 2010-02-12
Form your post i understand that you have CUPS configured in your Ubuntu system.

1)Ubuntu Configuration

   i) Finding the link you need to use for configuring the  printer in windows
      
      -> You can goto [http://localhost:631](http://localhost:631) in any browser
      -> Goto Administration in the web page and click Manage printers. It will be showing the printers as links. While moving the mouse pointer to the link, 
         you can see a URL in the status bar .Note down the URL, because it is 
         needed while configuring this printer in windows

   ii) Other settings in Ubuntu machine
      -> Goto Gnome Menu-> Administration -> Printing
         A window will open
      -> Click on Server -> settings
         Another window will open
      -> Enable The following check boxes
           1) Publish Shared printers connected to the system
           2) Allow printing from the internet  
      
2)Windows Configuration
 
   i) Goto start mneu -> Printers and faxes -> Add a printer
  ii) Select "A network printer, or a printer attached to another computer" and
      click next
 iii) Select "Connect to a printer on the Internet or on a home or office
      network"
  iv) Enter the URL you have noted down in the windows system and click next
   V) It will be showing a window to install the drivers either by selecting in the list 
      or from a disk (you can choose your option)
  vi) After installing the drivers you can select between setting this printer as default or not
 vii) Click finish

Now you can print from the windows machine and release the print jobs from CUPS

---

