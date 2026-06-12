---
title: "New to Mythbuntu"
date: 2010-04-26
forum: Mythbuntu
---

### Post by kazman on 2010-04-26
Hi I have been looking at creating a PVR and have just installed a fresh install of Mythbuntu 10.04RC (mythtv .23) on a VM and that went well. I am using HDHomerun for the TV which have connected and scanned all the channels successfully. 
 
I have a few questions. Forgive me if I am not clear.
 
I would like to watch Live TV and media via MythWeb as I work in the UK but have the server in Australia. Is this possible? I am really missing the Cricket and Rugby League :(
 
When I click on the ASX link in Mythweb I get a error as the link is like this [http://servername:9080//name_of_stream](http://servername:9080//name_of_stream) my issue is why is there two forward slashes? I don't know where that comes from. I am port forward from my router to the vm. I have setup the video being recorded to be transcoded. Since this I don't have the option to watch what I am recording via flash. 
 
Hope this makes sense. 
 
Thanks in advance.

---

### Post by azmyth on 2010-04-26
My links have the // as well in mythweb. It doesn't effect the stream being played or downloaded.

---

### Post by Lepy on 2010-04-26
I have a friend who setup his mythbox for a similar purpose. He wished to watch local programming while teaching in Thailand.

I haven't played too much with streaming outside of a lan frontend. However, I have noticed that vlc will not open the asx stream while totem does it just fine. See if a different media player fixes your error.

Also, you will probably need to forward ports on your router and setup some sort of hostname service (like dyndns) if your isp does not assign static ip addresses. Looks like you have already done this though.

---

### Post by kazman on 2010-04-29
Cheers I found the option in MythWeb to stream via flash. Works great!!!!!

---

