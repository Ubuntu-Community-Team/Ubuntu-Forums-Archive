---
title: "url redirection"
date: 2011-08-31
forum: Networking &amp; Wireless
---

### Post by snipe34 on 2011-08-31
This has been happening for a while, but as the computer in question is my local server and I don't use the browser often I ignored the problem. It's a Ubuntu 11.04 server and the browser is Firefox 6.0. It's running bind9 for the local dns, yes I know its excessive for a small LAN. 
 
 
I wrote a script using wget to download a NOAA satellite image. This worked fine for most of the day. Now its resolving and connecting with a 302 Found redirect status, followed by search3.comcast.com which resolves the same (207.223.0.140:80) and connects with a 200 OK status. But that's the comcast search site not the NOAA site, and I don't get an image.
 
 
If I use firefox to open [www.swpc.noaa.gov/sxi/images/latest_sxi.png]("http://www.swpc.noaa.gov/sxi/images/latest_sxi.png") I get the search3.comcast.com page and the very first choice is [www.swpc.noaa.gov]("http://www.swpc.noaa.gov/"). Of course clicking on that link just refreshes the search3.comcast.com page. The same thing happens with any of the [www.swpc.noaa.gov]("http://www.swpc.noaa.gov/") pages listed. 
 
 
I can connect to the site using ie9 on a windows7 box and firefox 6 on my ubuntu laptop 11.04. The laptop can also connect using wget. 
 
 
I just opt-ed out of the comcast Domain helper and flushed the local DNS. I restarted both nscd and bind9 on the server, which should have flushed the local DNS and then restarted the server, just in case.
 
 
I don't understand why valid URLs being redirected, but what I find even more disturbing is that it worked for a while before it started being redirected.
 
I just tried wget from the command line using [http://satdat.ngdc.noaa.gov/sxi/archive/browse/goes15/2011/08/03/SXI_20110830_235600160_BA_15.PNG](http://satdat.ngdc.noaa.gov/sxi/archive/browse/goes15/2011/08/03/SXI_20110830_235600160_BA_15.PNG)
which worked, for now. This is a much more complicated way to get the image, owing to the location and file naming. 
 
I tried a nonsense URL and got the firefox page not found, but the noaa site url still gets the comcast search page.
 
Any ideas?
 
Tim

---

### Post by iponeverything on 2011-08-31
change the nameservers in the /etc/resolv.conf to be googles:

8.8.8.8
8.8.4.4

---

### Post by snipe34 on 2011-08-31
I just tried wget again from the command line and it worked and it worked from firefox. It's going to be one of those hard to naildown things.
 
I have 8.8.8.8 in my /etc/resolv.conf, and the router uses that as the secondary dns.  The only place the comcast dns servers are listed is far down on the list of bind9's named.conf.options, after googles dns servers.
 
 
 
Tim

---

