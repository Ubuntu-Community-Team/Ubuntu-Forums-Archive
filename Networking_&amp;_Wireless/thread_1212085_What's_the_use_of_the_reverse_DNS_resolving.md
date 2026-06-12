---
title: "What's the use of the reverse DNS resolving?"
date: 2009-07-13
forum: Networking &amp; Wireless
---

### Post by PryGuy on 2009-07-13
Good day everyone!
I'm now studying bind9 and I really can't get one thing: I have made a zone for archive.ubuntu.com (apt-mirror it locally). Everything was great though I had noticeable delays trying to ping it. Reply times were quite fast though. One of the guys on my local forum said I had to make the reverse DNS resolving.

I did it and it works fine now, but hey, why is that important 'cause as far as get it ping works the following way: you say 'ping google.com' for instance, ping resolves address, it's say 74.125.45.100 and that's about it, it knows the IP now, it can ping it by IP, so why the need for reverse DNS things?

Thank you in advance!

---

### Post by jonobr on 2009-07-14
Hello


I know that some sites and systems will reject requests if the ip address does not have reverse dns (specifically email).

If you get attention from a specifc IP address, reverse dns allows you to figure out the domain where its coming from.

Its not critical for configuration, but Im wondering if thats what you were experiencing, a remote site, trying to reverse dns you and not having success?

---

### Post by PryGuy on 2009-07-15
Well, I've found [a good article about it all]("http://www.crucialp.com/resources/tutorials/web-hosting/how-reverse-dns-works-rdns.php").

In my case 'ping host' fails if you try to reverse dns it and it's not configured.

---

