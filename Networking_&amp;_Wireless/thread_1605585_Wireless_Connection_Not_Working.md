---
title: "Wireless Connection Not Working"
date: 2010-10-25
forum: Networking &amp; Wireless
---

### Post by mcgilldh on 2010-10-25
Recently installed Ubuntu 10.04 on HP Pavillion ze5400.Wireless card is bcm94306MP. Wireless connection shows as disconnected. I am troubleshooting using the Ubuntu documentation on solving wifi problems. Ran ishw and it appears I do not have a driver properly installed. Obtained what I believe is the driver: bcmwl5.inf and bcmwl5.sys. Installed bcmwl5.inf using ndisgtk. I know its there as I can see it in System>admin>windows wireless drivers. However lshw still does not show it under configuration. I understand I must put the sys file in the same folder as where this inf file got installed. I assume all I do is copy and paste it into that folder. Is this correct? Next I need to find that folder. I tried the command find /home -name bcmwl5.inf and it did not show up. Can someone educate me just how to do this, that is find the folder and insert the sys file?

After I pass this hurdle then I will tackle trying to configure the card. Probably will need help with that also.

Please answer in an elemental way as I am not well versed in Ubuntu's processes.

---

### Post by zzantozz on 2010-10-25
I'm not sure what you're trying will solve your problem, as the ndis UI should set everything up properly. However, the reason you're not finding that file is that you're only searching files under the /home directory, and drivers, apps, and other system files typically live elsewhere. First, you should try locate instead of find because it's much faster:
```

locate bcmwl5.inf

```

The locate command uses a search index that is rebuilt every day by default, so if this file is a recent addition or if your computer tends to be off when the indexing is scheduled (early morning hours, I think), that may not find it. If not, then go ahead and use find. To search your entire file system, you should tell it "find /" instead of "find /home". However, running that as yourself will give you a lot of 'Permission denied' messages, so run it as root, and for best results, you'll want to be able to scroll through the results of the find in case other garbage shows up, so:
```

sudo find / -name bcmwl5.inf | less

```

Be prepared to wait a while (minutes perhaps) if you have a lot of files in your file system. If you have network drives or other resources mounted, like in /media, it will speed up the search if you unmount them first.

---

### Post by mcgilldh on 2010-11-01
Connection problem solved

I had to blacklist a competing driver...learned all this in ndiswrapper link from wifi problem solving instructions in the ubuntu documentation.

Next i had to erase all the wireless connections i had configured and then re establish them.

Now I am connnected to my network.....but can't get firefox to open any pages, so I am working on that.

Really think this all shouldn't have become such an arduous task and needs to be simplified.

---

