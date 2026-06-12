---
title: "BIND (named) DNS Error"
date: 2013-04-06
forum: Networking &amp; Wireless
---

### Post by altirisx on 2013-04-06
Alright so I followed a three part video tutorial on youtube called dansclasses, when I finished I tried to run the dns server by typing in the terminal ```
service named start
``` and it wouldn't start, I got this huge error:

```
 Starting named: 
Error in named configuration:
dns_rdata_fromtext: neccdata.com.zone:8: near 'IN': extra input text
zone neccdata.com/IN: loading from master file neccdata.com.zone failed: extra input text
zone neccdata.com/IN: not loaded due to errors.
_default/neccdata.com/IN: extra input text
dns_rdata_fromtext: neccdata.com.rr.zone:8: near '@': extra input text
zone 12.168.192.in-addr.arpa/IN: loading from master file neccdata.com.rr.zone failed: extra input text
zone 12.168.192.in-addr.arpa/IN: not loaded due to errors.
_default/12.168.192.in-addr.arpa/IN: extra input text
zone localhost.localdomain/IN: loaded serial 0
zone localhost/IN: loaded serial 0
zone 1.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.ip6.arpa/IN: loaded serial 0
zone 1.0.0.127.in-addr.arpa/IN: loaded serial 0
zone 0.in-addr.arpa/IN: loaded serial 0
                                                           [FAILED]]
```

Here is a cat scan of my neccdata.com.zone (Forward lookup zone)

```
$ORIGIN neccdata.com.
$TTL 86400
@    IN    SOA    dns1.neccdata.com.  hostmaster.neccdata.com. (
    2001062501 ;serial
    21600    ;refresh after 6 hours
    3600    ;retry after 1 hour 
    604800    ;expier after 1 week
    86400    ;minimum TTL 1 day

    IN    NS    dns1.neccdata.com.

    IN    MX    10    mail.neccdata.com.

    IN    A    192.168.12.177

dns1    IN    A    192.168.12.177

necc-centos    IN    A    192.168.12.177

ftp    IN    A    192.168.12.177

mail    IN    CNAME    necc-centos

www    IN    CNAME    necc-centos
```


Here is a cat scan of my neccdata.com.rr.zone (Reverse lookup zone)

```
$ORIGIN 12.168.192.in-addr.arpa.
$TTL 86400
@    IN    SOA    dns1.neccdata.com.  hostmaster.neccdata.com. (
    2001062501 ;serial
    21600    ;refresh after 6 hours
    3600    ;retry after 1 hour 
    604800    ;expier after 1 week
    86400    ;minimum TTL 1 day

@    IN    NS    necc-centos.neccdata.com.

1    IN    PTR    necc-centos.mail.neccdata.com.

2    IN    PTR    necc-centos.neccdata.com.

3    IN    PTR    necc-centos.neccdata.com.

4    IN    PTR    necc-centos.neccdata.com.
```

---

### Post by altirisx on 2013-04-06
Sorry to bump, I know this is a lot to look at but if someone could just tell me what the error message that is good enough for me, I am thinking it is saying I have an unecessary IN or something near the word named IN and the same for the symbol @. Thanks Guys please respond!

---

### Post by SeijiSensei on 2013-04-06
You need a closing parenthesis after the TTL and before the first NS record.

Usually it is considered polite here to wait a day before bumping your thread.

---

### Post by Doug S on 2013-04-06
Have a look at the [ubuntu server guide chapter on DNS.]("https://help.ubuntu.com/12.10/serverguide/dns.html") (I prefer the [PDF]("https://help.ubuntu.com/12.10/serverguide/serverguide.pdf") version)
Toss out your $ORIGIN statements, lots of tutorials have them, but I have yet to see them work properly.
Are you editing your files on a windows computer? make sure line termination methods are linux and not windows. You might need to do something like:```
cp all_batch all_batch.bak
tr --delete '\r' <all_batch.bak >all_batch
rm all_batch.bak
```There are tools to help, but I do things with basics. I do not know if this is the source of your extra input text errors or not.

I don't have time at the moment to really look at your files (maybe in about 6 hours I will), but I do see that you don't seem to have the serial numbers right, given that your are using date and rev number per date method. In the meantime, you can search by my user name and keyword "bind9" and you should find serveral examples where I have given configuration file examples (not that I am some big expert).

Edit: I see Seiji gave a better and shorter reply while I was off typing...

---

### Post by Doug S on 2013-04-06
I do not understand your reverse file, as it does not correlate at all with your forward file. This is what I would do for the two files:```
;
; BIND data file for neccdata.com
;
$TTL 86400
@       IN      SOA     neccdata.com. hostmaster.neccdata.com. (
                        2013040601      ; Serial
                        21600           ; Refresh
                        600             ; Retry
                        604800          ; Expire
                        86400 )         ; Minimum TTL
                IN      A       192.168.12.177
;
@               IN      NS      dns1.neccdata.com.
        IN      MX      10      mail.neccdata.com.
dns1            IN      A       192.168.12.177
necc-centos     IN      A       192.168.12.177
ftp             IN      A       192.168.12.177
mail            IN      A       192.168.12.177
www             IN      A       192.168.12.177
``````
;
; BIND reverse data file for local 192.168.12.XXX net
;
$TTL 86400
@       IN      SOA     dns1.neccdata.com. hostmaster.neccdata.com. (
                        2013050601      ; Serial
                        21600           ; Refresh
                        3600            ; Retry
                        604800          ; Expire
                        86400 )         ; Minimum TTL
;
@       IN      NS      dns1.neccdata.com.
177     IN      PTR     dns1.neccdata.com.
2       IN      PTR     some_future_computer.neccdata.com.
```

---

### Post by altirisx on 2013-04-09
Wow you guys are fing awesome, I'm going to try everything and reply back.

EDIT: I see what I did wrong, the guy in the vide did have a close parethesis and I didnt, I guess I didnt notice that. For the guy that gave me the zone files, thanks, I restarted named (bind) and it works. To tell you the truth I don't really understand what I am doing (which may be a problem) but in the future I will probably be following that Ubuntu guide you gave me, the one thing I don't quite understand is the serial. I readon the Ubuntu guide that the serial is usually year/month/day and I noticed that when you sent me the zone files, they had 20130406 but then they had 01 at the end. What is the 01? The other thing I noticed is that on the reverse lookup zone file you put 20130506 and then followed by 01. Was that a type-o or is it that when it expires or something?

Either way thanks a bunch!

---

### Post by Doug S on 2013-04-09
The 01 at the end is just the revision number for that day, in case you do several edits in one day, which one typically does while trying to figure this stuff out.
The 2013050601 serial number was a typo, I keep thinking May, but is it April.

---

### Post by SeijiSensei on 2013-04-09
One way to restart named is to send it the "HUP" signal like this:
```
sudo killall -HUP named
```
which forces the daemon to reread its configuration files.  It uses the serial number on each zone file to determine whether that zone needs updating.  So if you makes changes to a zone file, it is important to make sure the serial number for the new data is larger than the serial number on the existing data.  Many of us use the YYYYMMDDNN approach so we can increment the last two digits if multiple zone file edits occur within a single day.

If you restart the server with 
```
sudo service bind9 restart
```
that shuts down the daemon and restarts it with the most recent zone files.  In that case the additional version number is not important.

---

