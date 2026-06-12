---
title: "ISP's hijacking DNS. Here's my solution."
date: 2009-08-05
forum: Networking &amp; Wireless
---

### Post by MechaMechanism on 2009-08-05
So now we have Comcast hijacking DNS based on this Slashdot posting below.  They are joining a terrible club that causes disruption for all kinds of software that depends upon a proper response.  Sometimes software will receive an DNS error and in response to that it will change it's behaviour and now we have DNS hijacking screwing this up.

[http://tech.slashdot.org/story/09/08/05/1926257/Comcast-the-Latest-ISP-To-Try-DNS-Hijacking](http://tech.slashdot.org/story/09/08/05/1926257/Comcast-the-Latest-ISP-To-Try-DNS-Hijacking)
[http://tech.slashdot.org/story/09/08/04/1512248/Bell-Starts-Hijacking-NX-Domain-Queries](http://tech.slashdot.org/story/09/08/04/1512248/Bell-Starts-Hijacking-NX-Domain-Queries)

Here is my solution that I have been using for some time.  I use my own DNS for reasons other than hijacking but it should help the anti-hijackers.




Open Synaptic and do a search for bind9 and select install.
Then open your terminal and do...
```
sudo /etc/init.d/bind9 stop
```Now we will edit 2 files.
```
sudo nano /etc/bind/named.conf.options
```make the file "named.conf.options" like the one below.  Take care to not touch the forwarders options, just leave the forwarders alone, meaning they should be commented out and all zeroes.
```
options {
    directory "/var/cache/bind";

    // If there is a firewall between you and nameservers you want
    // to talk to, you may need to fix the firewall to allow multiple
    // ports to talk.  See http://www.kb.cert.org/vuls/id/800113

    // If your ISP provided one or more IP addresses for stable 
    // nameservers, you probably want to use them as forwarders.  
    // Uncomment the following block, and insert the addresses replacing 
    // the all-0's placeholder.

    // forwarders {
    //     0.0.0.0;
    // };

    auth-nxdomain no;    # conform to RFC1035
        listen-on { 127.0.0.1; };
        listen-on-v6 { ::1; };
        allow-query { 127.0.0.1; };
        allow-transfer { none; };
        allow-recursion { 127.0.0.1; };
        dnssec-enable yes;
        dnssec-validation yes;
        dnssec-lookaside . trust-anchor dlv.isc.org.;
};
```Now edit the file "named.conf.local"
```
sudo nano /etc/bind/named.conf.local
```Make the file "named.conf.local" like the one below.
```
//
// Do any local configuration here
//

// Consider adding the 1918 zones here, if they are not used in your
// organization
//include "/etc/bind/zones.rfc1918";
logging {
category lame-servers { null; };
};
//
trusted-keys {
 dlv.isc.org. 257 3 5 "BEAAAAPHMu/5onzrEE7z1egmhg/WPO0+juoZrW3euWEn4MxDCE1+lLy2
                       brhQv5rN32RKtMzX6Mj70jdzeND4XknW58dnJNPCxn8+jAGl2FZLK8t+
                       1uq4W+nnA3qO2+DL+k6BD4mewMLbIYFwe0PG73Te9fZ2kJb56dhgMde5
                       ymX4BI/oQ+cAK50/xvJv00Frf8kw6ucMTwFlgPe+jnGxPPEmHAte/URk
                       Y62ZfkLoBAADLHQ9IrS2tryAe7mbBZVcOwIeU/Rw/mRx/vwwMCTgNboM
                       QKtUdvNXDrYJDSHZws3xiRXF1Rf+al9UmZfSav/4NWLKjHzpT59k/VSt
                       TDN0YUuWrBNh";
};
```Now we restart bind9

```
sudo /etc/init.d/bind9 start
```
Now we need to change network manager to use the new DNS server.
Right click the network icon and select "Edit Connections"
On the tab "Wired" select your connection.  Most likely to be "Auto eth0"
Select "Edit" button on right side.
Enter password when prompted.
Select tab "IPv4 Settings"
In method box select "Automatic (DHCP) address only"
In box "DNS Servers:" enter 127.0.0.1
In box "Search Domains:" enter your hostname.  Make sure your hostname is made up by you and not supplied by your ISP.  Also your hostname can be any made up nonsense like "bozo-the-clown"
Leave the box "DHCP Client ID:" alone, do not mess with it.
Click apply.

Reboot is probably good idea at this point.

For users who use wireless and other connections, please tell us how you got it to work.  I only use wired and have no experience with other connection types.

---

### Post by starcannon on 2009-08-05
The thing that telco's and cable companies can't seem to wrap their head around is that for every nasty idea they conceive, there will likely be 10 work around solutions cooked up within a week. They spend millions trying to suck even more money from their already over milked costumers, then spend a yearly budget trying to stay one step ahead of the work around solutions.

/sigh.

---

### Post by Hobgoblin on 2009-08-05
> **MechaMechanism said:**
> Take care to not touch the forwarders options, just leave the forwarders alone, meaning they should be commented out and all zeroes.


I'm confused here, surely you need valid DNS servers outside your own network for your local DNS server to refer to for addresses it does not know?

---

### Post by calrogman on 2009-08-05
> **Hobgoblin said:**
> I'm confused here, surely you need valid DNS servers outside your own network for your local DNS server to refer to for addresses it does not know?

[ dlv.isc.org]("https://dlv.isc.org/")

---

### Post by slakkie on 2009-08-05
opendns anyone?

---

### Post by MechaMechanism on 2009-08-05
> **Hobgoblin said:**
> I'm confused here, surely you need valid DNS servers outside your own network for your local DNS server to refer to for addresses it does not know?You do not need any DNS servers because bind9 contacts the root servers directly.

> **calrogman said:**
> [ dlv.isc.org]("https://dlv.isc.org/")The dlv is just a registry for secure DNS.

---

### Post by kieransimkin on 2009-08-05
> **Hobgoblin said:**
> I'm confused here, surely you need valid DNS servers outside your own network for your local DNS server to refer to for addresses it does not know?

Yes, but that DNS server doesn't have to be your ISP's. If you run your own copy of Bind, by default it'll query the root servers first and then follow the DNS hierarchy down until it gets an answer - it basically follows the same process your ISP's DNS server would be doing for you. (if it weren't nobbled by DNS hijacking)

---

### Post by MechaMechanism on 2009-08-05
> **slakkie said:**
> opendns anyone?OpenDNS works by hijacking DNS.

---

### Post by Hobgoblin on 2009-08-05
> **MechaMechanism said:**
> You do not need any DNS servers because bind9 contacts the root servers directly.


Ah thanks.

I thought that was regarded as something one should not do though so as not to overload the root servers?

---

### Post by J panic on 2013-02-16
Is there a solution betwixt the two?  Allowing one to keep anti-[whateveryouplease] from 'those' resolvers while not fetching the ad bits on NX?

perhaps having several resolver check at once ignoring the one that returns varying results (likely NX hijack?) ?

sure, there are probably some lovely anti-[whatever] software that can be installed locally but I hope to have this curiosity sated well first :)

---

### Post by papibe on 2013-02-16
This is very old thread. Feel free to create a new one and link this one if feel like it.

For now, because of _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

**Thread Closed**.

---

