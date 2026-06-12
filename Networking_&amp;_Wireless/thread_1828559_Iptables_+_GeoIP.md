---
title: "Iptables + GeoIP"
date: 2011-08-19
forum: Networking &amp; Wireless
---

### Post by nathema on 2011-08-19
Hi,

Yesterday I installed xtables-addons on my Ubuntu Server 10.04 box, to be allow my SSH port per country. 
```
iptables -A INPUT -p tcp --dport 22 -m geoip --src-cc NL -j ACCEPT
```results in:
```
Could not open /var/geoip/LE/NL.iv0: No such file or directory
iptables v1.4.4: Could not read geoip database
```Following article [http://www.debian-administration.org/articles/518](http://www.debian-administration.org/articles/518) from 2007 for debian, i tried performing steps 5 and 6, hoping this would result in the proper files. But instead i got:
```
geoipdb.bin  geoipdb.idx
```How do I set up the correct geoip database. If there is a package that presents me an outdated version, I'm quite happy with that.

---

### Post by nathema on 2011-08-22
I still have no luck finding a package or download providing the /var/geoip/* structure needed bij iptables geoip module (xtables-addons package). Anyone an idea?

---

### Post by nathema on 2011-08-26
Can't believe nobody uses this feature

---

### Post by nathema on 2011-08-26
Current status!

I managed to fix the geoip database for xtables:
```

aptitude install libtext-csv-xs-perl xtables-addons-common # added xtables-addons-common for completeness of the example

mkdir -p /var/geoip/LE /usr/src/GeoIP 
wget -O /usr/src/GeoIP/GeoIPCountryCSV.zip http://geolite.maxmind.com/download/geoip/database/GeoIPCountryCSV.zip 
wget -O /usr/src/GeoIP/csv2bin-20041103.tar.gz http://people.netfilter.org/peejix/geoip/tools/csv2bin-20041103.tar.gz 
wget -O /usr/src/GeoIP/xtables-addons-1.21.tar.bz2 http://downloads.sourceforge.net/project/xtables-addons/1.21/xtables-addons-1.21.tar.bz2   

cd /usr/src/GeoIP 
tar xf csv2bin-20041103.tar.gz unzip GeoIPCountryCSV.zip

```Also put the following perl file in the /usr/src/GeoIP directory (filename: geoip_csv_iv0.pl)
```
#!/usr/bin/perl
#
#       Converter for MaxMind CSV database to binary, for xt_geoip
#       Copyright Â© Jan Engelhardt <jengelh@medozas.de>, 2008
#
#       Use -b argument to create big-endian tables.
#
use Getopt::Long;
use IO::Handle;
use Text::CSV_XS; # or trade for Text::CSV
use strict;

my %country;
my %names;
my $csv = Text::CSV_XS->new({binary => 0, eol => $/}); # or Text::CSV
my $mode = "VV";

&Getopt::Long::Configure(qw(bundling));
&GetOptions("b" => sub { $mode = "NN"; });

while (my $row = $csv->getline(*ARGV)) {
        if (!defined($country{$row->[4]})) {
                $country{$row->[4]} = [];
                $names{$row->[4]} = $row->[5];
        }
        my $c = $country{$row->[4]};
        push(@$c, [$row->[2], $row->[3]]);
        if ($. % 4096 == 0) {
                print STDERR "\r\e[2K$. entries";
        }
}

print STDERR "\r\e[2K$. entries total\n";

foreach my $iso_code (sort keys %country) {
        printf "%5u ranges for %s %s\n",
                scalar(@{$country{$iso_code}}),
                $iso_code, $names{$iso_code};

        open(my $fh, ">".uc($iso_code).".iv0");
        foreach my $range (@{$country{$iso_code}}) {
                print $fh pack($mode, $range->[0], $range->[1]);
        }
        close $fh;
}

```And we continue:
```
cd /usr/src/GeoIP/csv2bin 
make

cd /var/geoip 
/usr/src/csv2bin/csv2bin /usr/src/GeoIP/GeoIPCountryWhois.csv   

cd /var/geoip/LE 
perl /usr/src/GeoIP/geoip_csv_iv0.pl /usr/src/GeoIP/GeoIPCountryWhois.csv
```Ok the database is made.
But now we have a nasty problem:
```
root@orestes:~# iptables -A INPUT -p tcp -m geoip --src-cc CN -j DROP
iptables: No chain/target/match by that name.
```Iptables does not recognize geoip as match module. 
```
root@orestes:~# cat /proc/net/ip_tables_matches
multiport
multiport
recent
udplite
udp
tcp
state
icmp
```
Iptables -m geoip --help does show geoip related help.

I also don't see it in lsmod:
```
root@orestes:~# lsmod
Module                  Size  Used by
xt_multiport            2794  0
xenfs                   6105  1
xt_recent               8218  0
xt_tcpudp               2667  13
nf_conntrack_ipv6      12770  11
nf_conntrack_ipv4      12742  12
nf_defrag_ipv4          1481  1 nf_conntrack_ipv4
xt_state                1490  23
nf_conntrack           73326  3 nf_conntrack_ipv6,nf_conntrack_ipv4,xt_state
ip6t_LOG                5649  2
ipt_LOG                 5370  2
ip6table_filter         1712  1
ip6_tables             19428  2 ip6t_LOG,ip6table_filter
iptable_filter          1841  1
ip_tables              18201  1 iptable_filter
lp                      9336  0
x_tables               22361  8 xt_multiport,xt_recent,xt_tcpudp,xt_state,ip6t_LOG,ipt_LOG,ip6_tables,ip_tables
parport                37160  1 lp
xen_netfront           17890  0
xen_blkfront           10697  5
```

---

### Post by LPopov on 2011-09-01
I had the same problem, your posts helped me a lot.
For the "iptables: No chain/target/match by that name." error - instead of downloading xtables-addons-1.21.tar.bz2 you should install  xtables-addons-source. Then run
```
sudo module-assistant --verbose --text-mode auto-install xtables-addons
```
and it will build and install the necessary modules. After that iptables will work fine with geoip :).

---

### Post by nathema on 2011-09-01
> **LPopov said:**
> I had the same problem, your posts helped me a lot.
For the "iptables: No chain/target/match by that name." error - instead of downloading xtables-addons-1.21.tar.bz2 you should install  xtables-addons-source. Then run
```
sudo module-assistant --verbose --text-mode auto-install xtables-addons
```and it will build and install the necessary modules. After that iptables will work fine with geoip :).

Thanks! Just what I needed!

Now I'm gonna try to get it working with ip6tables, 'cuz my pizzabox has both.

---

### Post by georgian_craciun on 2011-11-11
Or like [HERE]("http://scripturi-instalare-ubuntu.blogspot.com/2011/10/vor-intre-strainii-la-voi-in-casa.html")  (only for [COLOR=red]Ubuntu 10.04 Lucid Lynx LTS)
[COLOR=Black]Download script, [/COLOR][/COLOR]make it executable and run it (with sudo).
That's all. Now xtables with GeoIP is functional.

[COLOR=red][/COLOR]

---

### Post by linuxcimber on 2012-11-03
Hi,

I've just upgraded to Kubuntu 12.10, it seems like they have let the xtables version at 1.42, so currently geoip will not work. The only quick workaround was to download the latest version of xtables, tar -xvJf, ./configure, make, make install then reboot and then geoip is working again. 

Still, I don't understand why they didn't upgrade the xtables version too, since they upgraded to kernel 3.5.

---

