---
title: "apt-cacher-ng and PPAs, also use on server"
date: 2012-10-05
forum: Networking &amp; Wireless
---

### Post by drknot on 2012-10-05
I have set up apt-cacher-ng on a headless server on my LAN and it is working fine out of the box.

I want to add the Stellarium and WINE PPAs.
I have created an additional url list in the appropriate place, but not sure I have truncated at the correct place
file contains the following two URLs
[http://ppa.launchpad.net/stellarium/stellarium-releases/ubuntu](http://ppa.launchpad.net/stellarium/stellarium-releases/ubuntu) precise main [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) precise main 
Not sure they are working - how do I check and if you have it set up what did you do?
Should I have truncated at the last backslash  ie ....releases/ and ....ppa/


Secondly, should I redirect via the proxy on the actual server as well or will I create an issue for myself. I think it should be OK to do this but would like some reassurance

I run 12.04LTS on 4 machines (2 are xubuntu netbooks), 12.04LTS server edition on the server.  This is already making a massive dent in my limited broadband (2Gb/month)

Thanks

---

### Post by papibe on 2012-10-05
Hi drknot.

How did you set up apt-cacher-ng?
Did you set a proxy using the 'Acquire' statement or did you change the sources?

Usually source files start with 'deb', for instance:
```
deb  http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu precise main
```

> **drknot said:**
> Secondly, should I redirect via the proxy on the actual server as well or will I create an issue for myself.

I won't create an issue. I would recommend setting up the server to also going through the proxy. That's the way I do it, BTW.

Let us know how it goes.
Regards.

---

### Post by drknot on 2012-10-06
I set it up using the aquire statement on the two netbooks. I have also set the proxy in Synaptic on one of them. 

   The manual lists the urls without a preceding deb and I have inspected the lists in /etc/apt-cacher-ng/   from the manual (sorry I struggle to quote properly)   &quot;URL lists and remote repository list files. The file names are arbitrary, no special suffix is expected. They are included during processing of configuration files and can contain data in one the following formats:      simple text files with one URL per line (the URL should point to the base directory of the repository, e.g. &quot;[http://ftp.de.debian.org/debian/&quot;](http://ftp.de.debian.org/debian/&quot;)). A URL must start with http:// and should end with a slash     an RFC822-like format, with lines like 'Site: ' and 'Archive-http: /base/directory/of/repository/'. Optional fields are also used in this remapping descriptions to add more possible variants (Alias, Aliases, X-Archive-http:) of the URLs to the lookup list&quot; 

    I have subsequently found :
 [http://opencomputing.blogspot.co.uk/2010/07/speeding-up-your-updates-with-ubuntu.html](http://opencomputing.blogspot.co.uk/2010/07/speeding-up-your-updates-with-ubuntu.html)

 which sorts out much of my query. I have spent days looking at sites before this one. It looks like I may need to put a remap into my .conf as well as specifying the URL

 Thanks for your help

---

### Post by papibe on 2012-10-09
I think it may be easier than you think.

Let me use an example. Let's say everything is working OK before adding the ppa on one of the laptops, and that you want to install the package 'mediainfo' from here 'ppa:shiki/mediainfo'.

In one laptop, you add the ppa to its sources:
```
sudo add-apt-repository ppa:shiki/mediainfo
```
In order to let apt-proxy-ng to cache the sources' index files, you simply just update:
```
sudo apt-get update
```
That would get the index files cached on the server.

Then you can install the application:
```
sudo apt-get install mediainfo
```
That would also cache the package on the server.

If you want to install it on the other laptop, you follow the exact same procedure. The difference will be that the index files and the package itself have been cached, thus it will be very fast, and you'll be saving bandwidth.

I hope that helps. Let us know how it goes.
Regards.

---

