---
title: "Wifi not accessable"
date: 2010-11-28
forum: Networking &amp; Wireless
---

### Post by Black_OuT on 2010-11-28
hei guys am new to ubuntu. i've downloaded 10.10 and installed the driver using a wired line.. and when i check in system > admin > additional drives

it shows broadcom sta .. and it shows the current status as driver installed but not currently in use..

i've tried many ways and check many threads but am unable to activate my wifi.
my wifi only worked the time i've installed it.. but after restarting my comp it just stoped searching for nearby networks.. its basically inactive and i can't do anything about it.
[IMG]http://%3Cdiv%20style=%22width:480px;text-align:right;%22%3E%3Cembed%20width=%22480%22%20height=%22360%22%20src=%22http://static.pbsrc.com/flash/rss_slideshow.swf%22%20flashvars=%22rssFeed=http%3A%2F%2Ffeed1182.photobucket.com%2Falbums%2Fx459%2Ffrostprodigy%2Ffeed.rss%22%20type=%22application/x-shockwave-flash%22%20wmode=%22transparent%22%20/%3E%3Ca%20href=%22http://photobucket.com/redirect/album?showShareLB=1%22%20target=%22_blank%22%3E%3Cimg%20src=%22http://pic.photobucket.com/share/icons/embed/btn_geturs.gif%22%20style=%22border:none;%22%20/%3E%3C/a%3E%3Ca%20href=%22http://s1182.photobucket.com/albums/x459/frostprodigy/%22%20target=%22_blank%22%3E%3Cimg%20src=%22http://pic.photobucket.com/share/icons/embed/btn_viewall.gif%22%20style=%22border:none;%22%20/%3E%3C/a%3E%3C/div%3E[/IMG][IMG]http://s1182.photobucket.com/albums/x459/frostprodigy/[/IMG]
[IMG]http://ubuntuforums.org/[IMG]http://i1182.photobucket.com/albums/x459/frostprodigy/image.png[/IMG][IMG]http://i1182.photobucket.com/albums/x459/frostprodigy/image.png[/IMG]

any suggestions ?

---

### Post by Black_OuT on 2010-11-28
basically the question is how do i switch on my wifi .. 
im using acer 4740 travelmate i3-350M processor

---

### Post by johnmay on 2010-11-28
Install WINE and then use the windows driver from there. It allows NDISwrapper to use the driver. Also, where did you get that desktop picture?

---

### Post by Black_OuT on 2010-11-29
hmm.. the driver is already installed into the kernal.. and how can i call in windows driver using wine ? 

am kinda new so please bare with the newbieness.. 

as for the pic - [http://www.google.co.in/imgres?imgurl=http://acidzburns.files.wordpress.com/2009/09/01624_thecityofathousandminaret_1680x1050.jpg&imgrefurl=http://acidzburns.wordpress.com/2009/09/09/favourite-wallpapers-collection-courtesy-of-interfacelift/&usg=__2gARugpUdSaiwDWJ9lD76-xVXYo=&h=1050&w=1680&sz=1017&hl=en&start=0&zoom=1&tbnid=gpke36_6clhA5M:&tbnh=108&tbnw=172&prev=/images%3Fq%3Dcool%2Bhd%2Bwallpapers%26um%3D1%26hl%3Den%26safe%3Doff%26sa%3DX%26biw%3D1366%26bih%3D575%26tbs%3Disch:1&um=1&itbs=1&iact=rc&dur=397&ei=R2rzTM_DLJLRcPTGiP4J&oei=R2rzTM_DLJLRcPTGiP4J&esq=1&page=1&ndsp=19&ved=1t:429,r:2,s:0&tx=92&ty=48](http://www.google.co.in/imgres?imgurl=http://acidzburns.files.wordpress.com/2009/09/01624_thecityofathousandminaret_1680x1050.jpg&imgrefurl=http://acidzburns.wordpress.com/2009/09/09/favourite-wallpapers-collection-courtesy-of-interfacelift/&usg=__2gARugpUdSaiwDWJ9lD76-xVXYo=&h=1050&w=1680&sz=1017&hl=en&start=0&zoom=1&tbnid=gpke36_6clhA5M:&tbnh=108&tbnw=172&prev=/images%3Fq%3Dcool%2Bhd%2Bwallpapers%26um%3D1%26hl%3Den%26safe%3Doff%26sa%3DX%26biw%3D1366%26bih%3D575%26tbs%3Disch:1&um=1&itbs=1&iact=rc&dur=397&ei=R2rzTM_DLJLRcPTGiP4J&oei=R2rzTM_DLJLRcPTGiP4J&esq=1&page=1&ndsp=19&ved=1t:429,r:2,s:0&tx=92&ty=48)

just googled "hd wallpapers"

---

### Post by johnmay on 2010-11-29
Install ndis-wrapper which is the gui for windows wireless. 

Download the windows driver for your wifi. Right clicking should bring you an option to open with WINE.
Install as normal.
Once installed, goto: System->Administration->Windows Wireless Drivers and load the .inf file that is located in home/youraccounthere/.wine(#hiddenfile -show hidden files to see)/c_drive/Program Files      more or less

make sure that the 'card' is on if you have that option. 

weave a circle round it thrice and close your eyes with holy dread

---

