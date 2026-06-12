---
title: "Automatic wireless connections undesirable"
date: 2011-01-25
forum: Networking &amp; Wireless
---

### Post by phoenixstormcrow on 2011-01-25
Can anyone tell me if there is a way to change the behavior of Network Manager, so that it will only automatically connect to certain wireless networks which I specify, and not automatically connect to others I may have previously used.  For example, there are a lot of wifi networks called "linksys", and I don't want the program to automatically try to connect to whichever one it finds.

If someone can tell me in which file(s) the list of these connections is stored, I might be able to write a script which will edit that list on startup.  Of course, if there is a simpler way, that would be better.

Thanks in advance,
phoenixstormcrow

---

### Post by Cheesehead on 2011-01-25
Right-click on the NM icon
Select 'Edit Connections'
A list will open up.

1) Delete (button) all the networks you don't ever want to connect to again. This will clean out the list and leave you with only desired networks.

2) Edit (button) the remaining items - specifically common duplicates like 'linksys'. Uncheck the 'connect automatically' box. Now your 'linksys' entry will still have WEP and other essential info, but won't try to connect until you tell it to.

---

