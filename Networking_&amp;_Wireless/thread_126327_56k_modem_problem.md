---
title: "56k modem problem"
date: 2006-02-06
forum: Networking &amp; Wireless
---

### Post by Razorback on 2006-02-06
I recently purchased a Hayes external 56k modem to replace an existing internal winmodem that I had in my linux box.  Everything went great with the modem being found and easily configured with wvdial.  But when I launch via sudo wvdial, I have problems.  It connects to my ISP just fine but acts like no communications occur.  Firefox times out on all webpages. When watching the network status of the modem, it showed as being idle with an occasional received showing up.  Being new to linux, I am kind of stumped as to what I need to do to check this out or has anyone else run into this.  Thanks for any help.

---

### Post by Razorback on 2006-02-08
Anyone have any ideas?

---

### Post by AmboyGuy on 2006-02-08
Just to make sure that your Firefox preferences are correct:
In Firefox:
**Edit > Preferences >General > Connection Settings ::** set 'direct connection'
**Edit > Preferences > Advanced > Security ::** make sure all three protocols are checked.
**Edit > Preferences > Privacy > Cookies ::** Allow sites to set cookies & Keep Cookies :: I use 'ask me every time'
Then clear your private data ( cache, history, forms etc )
That should have firefox set up pretty well for the internet connection.

I use gnome-ppp to establish my connection to the internet. You can use Gnome's ** System > Administration > Networking ** to set up your modem properties. ( port, tone or pulse dialing etc.) For some reason this is an important step, it must set a system variable that points requests to the serial port where wvdial didn't appear to do that for me.

---

### Post by Razorback on 2006-02-08
Thanks for the reply.

I was using gnome-ppp also.  What is strange is that synaptic also times out when trying to reload the repositories.  I can see the connection made with wvdial and here the modem connecting.  I see my ISP's DNS servers IP's thru wvdial but when I ping the IP's, I get no response.  I am really confused.  Is there a log that shows what is going on?  Could firestarter be causing problems?  I haven't really tweaked with it.

Also, I will check out my Firefox settings.

---

### Post by swimmerbody on 2008-04-11
Did you find the answer to this problem.  I am having the same difficulty.  Using Ubuntu 8.04 which has Firefox 3.0.

---

