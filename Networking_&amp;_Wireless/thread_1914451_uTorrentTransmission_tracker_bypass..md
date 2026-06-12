---
title: "uTorrent/Transmission tracker bypass."
date: 2012-01-24
forum: Networking &amp; Wireless
---

### Post by Kyslosh on 2012-01-24
Hello, post is not only for Linux but also for windoze.
Any kind of client (uTorrent, Bittorent, Transmission...)

My problem is really simple, is it possible to "bypass" tracker? 
(by bypassing I mean skip step of initializing torrent via tracker)

Better question would be: Is there any online service that shows IP : port list (peer/seed list) of desired torrent?
So I would copy paste my peers/seeds manually.

All this because I just figured out that my internet provider (dorm room) blocks/redirects torrent trackers only.
```
ping www.tracker.thepiratebay.org 
Pinging tracker.thepiratebay.org **[127.0.0.1]** with 32...
```(I am on Windows)

I can download torrents normally (without tracker) when I hibernate my computer while downloading any kind of torrent (where trackers work home/public WIFI etc.) and wake up computer while plugged in to dorm network. (and I get nice speeds 4mb/s etc.)

I tried rebuild packet that is uTorrent sending and try it on free hosting.

[PHP]<?php
$fp = fsockopen("www.tracker.hexagon.cc", 2710, $errno, $errstr, 30); //2710 is port
if (!$fp) {
    echo "$errstr ($errno)<br />\n";
} else {
    $out = "GET /announce?info_hash=w%ab%de%15R%7cz%87%aeT%f15%fe%93%ce%1d%f8F%cf%ae&peer_id=-UT3000-%ced%f6_%df%ba%d2%b5Q%e7%14%7d&port=61379&uploaded=0&downloaded=0&left=367262626&corrupt=0&key=98DD03C6&event=started&numwant=200&compact=1&no_peer_id=1&ipv6=2002%3a93af%3ab008%3ab%3a98f1%3ab960%3ac0fd%3a8403  HTTP/1.1\r\n";
    $out .= "Host: tracker.hexagon.cc:2710\r\n";
    $out .= "User-Agent: uTorrent/3000(25806)\r\n";
    $out .= "Accept-Encoding: gzip\r\n";
    $out .= "Connection: Close\r\n\r\n";
    fwrite($fp, $out);
    while (!feof($fp)) {
        echo fgets($fp, 128);
    }
    fclose($fp);
}
?>[/PHP]But I get error 
```

HTTP/1.0 200 OK Content-Type: text/plain Content-Length: 85  d14:failure reason63:Requested download is not authorized for use with this tracker.e

```I do not even know what I was expecting to get via browser (I guess IP list or so) [stupid]

Any ideas?

Thanks ;)

---

### Post by Kyslosh on 2012-01-30
-- bump

---

