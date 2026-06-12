---
title: "DVB scanning with w_scan"
date: 2010-10-21
forum: Mythbuntu
---

### Post by mookie60 on 2010-10-21
Myth 9.04/.21 (up to date)
Hauppauge 1600 & pchdtv 5500

I get my QAM channels via cable.  Some channels, which I know exist (recently found with myth scan), were not found during a scan today.   I decided to trying using w_scan instead, as it seemed some people found this more reliable. 

So I ran w_scan and created the channels.conf file.   

   w_scan -a1 -fc -A2 -t3 >> channels.conf

The channel.conf file lists all kinds of channel data (though still not some of the channels I'd hoped to get).   I then used the backend-setup (input connections) to select the channels.conf file, instead of scanning.

After selecting the file and clicking "next", it still pops-up the myth scanning box, but no activity takes place - it just hangs.

Is this normal, or is something else suppose to happen?  The only way I can stop it is to hit escape.  

Also, I wanted to try dvbscan, but could not find it using apt-get or synaptic - how do I install it?   

Thanks,

---

### Post by ian dobson on 2010-10-22
Hi,

I think you need to use the -x option to get w_scan to create a file in a format that myth-setup can read.

See [http://www.gossamer-threads.com/lists/mythtv/dev/339853](http://www.gossamer-threads.com/lists/mythtv/dev/339853)

Regards
Ian Dobson

---

