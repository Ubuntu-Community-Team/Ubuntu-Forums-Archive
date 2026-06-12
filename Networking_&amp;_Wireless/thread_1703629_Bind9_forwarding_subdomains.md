---
title: "Bind9 forwarding subdomains"
date: 2011-03-09
forum: Networking &amp; Wireless
---

### Post by cpsully69 on 2011-03-09
Before the flames start, I know there are a lot of posts about Bind9 subdomains.  I've been looking around for days, trying different things, the advise thus far doesn't seem to help me.

I have a Linux server running Bind9 as my internal DNS server for 'myschool.edu'  This was a box that I adopted as part of my job.  I've only ever used something like Win2003 Server as DNS before.  Or, used an outsourced DNS provider.

Anyway, I'm being asked to pilot a new email solution for the school, and want to setup 'newmail.myschool.edu' sub-domain with MX records specific to that domain.  I've already added this domain and MX records to our externally hosted (Dreamhost) DNS provider.  Anyone externally can send emails to users on this new domain.

With my basic DNS knowledge, I thought the easiest thing to do would be to add newmail.myschool.edu to my named.conf file and set it to be a forwarder to the Dreamhost NS servers.  That seemed the least painful, most effective solution.  But, I cannot resolve newmail.myschool.edu internally.

Here is my named.conf file:
> // Custom named.conf - Robert Pyzalski - Sept 2008
// /etc/bind/named.conf

zone "." 
{ type hint;
  file "/etc/bind/db.root";
};

zone "localhost" 
{ type master;
  file "/etc/bind/db.local";
};

zone "127.in-addr.arpa" 
{ type master;
  file "/etc/bind/db.127";
};

zone "0.in-addr.arpa" 
{ type master;
  file "/etc/bind/db.0";
};

zone "255.in-addr.arpa" 
{ type master;
  file "/etc/bind/db.255";
};

zone "0.0.10.in-addr.arpa" 
{ type master;
  file "/etc/bind/db.0.0.10";
};

zone "5.0.10.in-addr.arpa"
{ type master;
  file "/etc/bind/db.5.0.10";
};

zone "myschool.edu" 
{ type master;
  file "/etc/bind/db.myschool.edu";
};
//HERE'S THE STUFF I ADDED FOR THE NEW SUBDOMAIN//
zone "newmail.myschool.edu"
{ type forward;
  forwarders {66.33.206.206; 66.201.54.66; };
};
//END NEW SUBDOMAIN STUFF//

options 
{ directory "/var/cache/bind";
  query-source address * port 53;

  forwarders 
  { ip_addresses_of_ISP_nameservers; };

  auth-nxdomain no;    # Conform to RFC1035
};

logging
{ channel default_log 
  { syslog local6;
    severity warning;
    print-time no;
    print-severity yes;
    print-category no;
  };
  category default
  { default_log;
  };
};

include "/etc/bind/zones.rfc1918";

Even after restarting, I can't resolve the new sub-domain.  Then when I dig, I get no answer, and it looks like it's my local server trying to answer, and not forwarding the query to dreamhost.

Any whitespace in front of lines are <tabs>, not spaces (in case that matters)

I've also tried putting this code before and after the main 'myschool.edu' zone statement. (wasn't sure if order mattered).

I get nothing in syslog indicating success or failure of the syntax of the named.conf file.

I'm at a loss where to go next, and would sure appreciate some help.

Thank you.
Chris

---

### Post by taget on 2011-05-05
Im assuming the mail server is local, if that is correct why not just have bind resolve to the internal address of the mailserver, instead if sending it out to Dreamhosts name server and then back again.

Just a thought, could be totally wrong. "shoots into darkroom" :)

---

### Post by SeijiSensei on 2011-05-05
Don't forward the subdomain.  Just add the appropriate records to the zone file for myschool.edu:

```

@    IN SOA myschool.edu. root.myschool.edu {
     [stuff]
}

[stuff]

newmail       IN NS ns.myschool.edu.
              IN NS ns2.myschool.edu.

              IN MX 0 newmailserver.myschool.edu.

newmailserver IN A 10.10.10.10

[stuff]

```

If you want to put the server in the subdomain, though you don't need to, replace "newmailserver" in the A record with "mailserver.newmail".

---

