---
title: "Sharing Printer to Windoes Clients clarification requested"
date: 2009-02-11
forum: Networking &amp; Wireless
---

### Post by Scunnered on 2009-02-11
Seeking information on another forum I was guided to this post

[http://ubuntuforums.org/showthread.php?t=268245](http://ubuntuforums.org/showthread.php?t=268245)

only to be informed that 
&#8220;*You are browsing a READ only archive of the main support categories pre 4/21/2008. You will not be able to post or reply any threads in this section*.&#8221;

The post was Sharing Printer to Windows Clients and below is the initial response provided

&#8220;[I]Save yourself some headaches (assuming this is a private network), edit the Listen directives in the following file:
(Dapper: /etc/cups/cups.d/ports.conf; Edgy: /etc/cups/cupsd.conf)
Code:
#Listen localhost:631
Listen *:631
Listen /var/run/cups/cups.sock
Restart the cups daemon:
Code:
sudo /etc/init.d/cupsys restart
On the Windows box:
Start the Add Printer wizard
Click Next
Select A network printer, or a printer attached to another computer
Select Connect to a printer on the Internet or on a home or office network
Type [http://server_name:631/printers/printer_name](http://server_name:631/printers/printer_name) in the URL box, where server_name is the hostname or ip address for the ubuntu machine, and printer_name is... the printer name. Don't forget the port number!
Click Next and run through the driver installation to complete

Should work just fine.
Last edited by mitch.c; December 4th, 2006 at 05:12 PM..[/I]&#8221;

This looked just what I needed but when I took matters further I found things that I was unsure of and posted seeking further information.  Unfortunately a response has not been forthcoming and as I am unable to add to the **post 268245** I will add my questions here.

Having looked at the first link it found that if I have done things right that in Ubuntu 8.10 it has the same file as for Edgy. When I open the cupsd.conf it displays as follows

LogLevel warning
SystemGroup lpadmin
# Allow remote access
Port 631
Listen /var/run/cups/cups.sock

would I be right in thinking that I have to insert the code detailed after # allow remote access and should I remove Port 631

For the Windows machine it currently has the printer properly set up do I remove this printer before I Start the Add Printer wizard ?
There is also a remark "Don't forget the port number" Am I right in thinking that this is 631?

If you could clarify these points I will follow this post and see what happens

[B]My original request for information was detailed as:
[/B]
I have a local printer (Epson Stylus Photo R265) connected to a Laptop via a USB connection and this works perfectly using Ubuntu 8.10. I wish to share this printer with my partner who is using XP via the wireless network that we have. 

I have tried various searches but they seem to be for Windows to Linux. I want my Ubuntu laptop to be the master and XP to be subservient in all matters.

I hope that I have not broken any unwritten rule regarding posting on different forums as I am desperate to seek a resolution to my problem.  If I have done so please advise accordingly. 

Can someone please advise what I need to do to achieve my aim?

Thanking you in anticipation

---

### Post by superprash2003 on 2009-02-11
you would need samba for this..
1) setting up samba - [http://www.prash-babu.com/2008/05/how-to-setup-samba-in-linux.html](http://www.prash-babu.com/2008/05/how-to-setup-samba-in-linux.html)
2) setting up printer sharing using samba - [http://www.prash-babu.com/2008/05/how-to-setup-network-printer-or-share.html](http://www.prash-babu.com/2008/05/how-to-setup-network-printer-or-share.html)

---

### Post by Scunnered on 2009-02-15
I am bumping this post in the hope that someone can assist by clarifying what I am required to do.  superprash offered 2 links but these involved completely working with the terminal, something that I am not comfortable in doing so.

As the clarification requested was for a small amount of text to be changed I was hopeful that with assistance I could safely make the changes and achieve a resolution to my problem.

I am somewhat out of my depth when faced with editing files or working with the terminal so anything that can be done to assist will be appreciated.

Thanking you in anticipation

---

### Post by Scunnered on 2009-03-03
bump

---

