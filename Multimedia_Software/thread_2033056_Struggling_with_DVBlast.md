---
title: "Struggling with DVBlast"
date: 2012-07-25
forum: Multimedia Software
---

### Post by Hughes365 on 2012-07-25
_Struggling with DVBlast _
   
  Never mention to your boss that you &#8216;once saw a server running ubuntu&#8217;, he might take that to mean you&#8217;re an expert. 
    
  Following the instructions on [Angry Technician&#8217;s guide to building a DVB IPTV sever]("http://angrytechnician.wordpress.com/2010/07/23/how-to-stream-every-channel-from-freeview-onto-your-network/"), I had reached the point where everything should boot up when Ethe0 comes online.  The stations were tuning properly aside from one or two (probably due to signal as others on the same multiplex were fine), I had set up the SAP server and the &#8216;Upstart&#8217; conf files were the last thing to go in&#8230; and then nothing happened. 
   
  To be specific, the Sap server starts up okay (so I'm fairly sure the .conf's are working) but the DVBlast streams do not.  Occasionally multiplex one on adapter0 would initialize at boot, but nothing else would.  
   
  After some careful investigation and a lot of frustration, I discovered that DVBlast couldn&#8217;t access /dev/dvb/adapter(x)/frontend0 without root permissions.  However, even changing the permissions through &#8216;chmod&#8217; for each adapter and subsequent folders did not allow anything but a sudo command to run the files.  What was more, any changes made to the permissions on these files within the &#8216;Adapter&#8217; subfolder reverts back to &#8216;none&#8217; for other users immediately upon reboot.  Perhaps the files are recreated every time the system boots?  I just don&#8217;t know.  
   
  So here&#8217;s the bottom line; I&#8217;m utterly stuck.  Having no prior knowledge of the OS, I honestly don&#8217;t know whether this is a simple problem with an easy fix, or a fundamental oversight in the demonstrated coding.  
   
  Whilst we could start each stream via vnc, it&#8217;d be kinda useless if we had to reinitialize all six multiplexes manually every time the server reset -_-&#8216;  

I suppose my real question comes down to this;  is there something I can do to either the inaccessible files or the upstart .conf&#8217;s that would allow DVBlast to run correctly upon boot?  Or perhapse there's another way of ensuring the streams run at startup?
   
  If you need any info on the details, just holler and I&#8217;ll post them up here asap, I really appreciate any help you can provide folks.
   
  Mike.

---

### Post by Hughes365 on 2012-07-26
Is this in the right place?  Should I move it to the server queries section?

---

