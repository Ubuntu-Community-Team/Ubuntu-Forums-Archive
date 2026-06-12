---
title: "samsung ML-2510 printer and SMC7004ABR barricade server"
date: 2009-08-28
forum: Networking &amp; Wireless
---

### Post by pctlinux on 2009-08-28
im newbie to ubuntu. it took me **3 MONTHS **!!! to finally get my samsung ml-2510 laser printer to work with an old and reliable SMC7004ABR barricade print server.
 
hope this post saves others the miseries i went thru.
 
im running Ubuntu 9.04. here what's you need to do
 
- system/administration/printing
- click 'new' (or 'new printer')
- expand '**network printer**'
- click **'LPD/LPR host or printer'**
- in 'host' input box, enter the IP and port of your SMC barricade print server
**192.168.x.yyy:515 **(for example, 192.168.1.133:515)
- in 'queues' input box, enter **LPT1** 
- click 'forward' (or 'apply')
- you should see a list of printer manufacturers
- scroll down till you see Samsung. click Samsung
- click 'forward'
- scroll down till you see ML-2510. click ML-2510
- you be presented with 2 samsung splix printer drivers. click the 'recommended' one
- click 'apply'.
- you're basically done. click the button to print a test page.
 
your ML-2510 should print. if it does not, just restart your ubuntu, and a page will print (the issue is more likely your SMC7004ABR print server needing a kick)
 
setting up printer to work with a print server in ubuntu requires that you know exactly what clicks or selections to pick! since i didnt know much about this stuff, it took me 3 months to find the right combinations above!
 
last not least, thanks to these 2 posts that helped me to find my way out of llinux printing miseries. if you have different models of printer and/or print server, these 2 posts may help.
[_[SIZE=2][COLOR=#0000ff][SIZE=2][COLOR=#0000ff]http://ubuntuforums.org/showthread.php?t=32692[/COLOR][/SIZE][/COLOR][/SIZE]_]("http://ubuntuforums.org/showthread.php?t=32692")
[_[SIZE=2][COLOR=#0000ff][SIZE=2][COLOR=#0000ff]http://ubuntuforums.org/showthread.php?t=516747[/COLOR][/SIZE][/COLOR][/SIZE]_]("http://ubuntuforums.org/showthread.php?t=516747")

---

