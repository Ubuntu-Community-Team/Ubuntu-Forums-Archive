---
title: "Ubuntu 12.04 version 1 apt-get update behind a proxy"
date: 2013-07-02
forum: Networking &amp; Wireless
---

### Post by jwp1 on 2013-07-02
Hi I setup a new 12.04 server.
I have a proxy that I have to go threw.

After install it remembered to the proxy address I could ssh out behind the proxy example [email]xxx@sdf.lonestar.org[/email]
This worked

I went to /etc/apt'
sudo nano apt.conf

added the lines in the special way.

made the adjustment to ect/profile to.

Got this error when I did sudo apt-get update

W: Failed to fetch [http://de.archive.ubuntu.com/ubuntu/dists/precise-backports/universe/i18n/Translation-en_US](http://de.archive.ubuntu.com/ubuntu/dists/precise-backports/universe/i18n/Translation-en_US)  Cannot initiate the connection to 8080:80 (0.0.31.144). - connect (22: Invalid argument)

Looking at the error I think some were it is 80 when it needs to be 8080

I really sure the apt is ok and the profile are ok and the bash.rc is ok

Not sure were the orignal config from the installation was written

Thanks

JWP

---

