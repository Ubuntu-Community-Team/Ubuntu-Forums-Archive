---
title: "ask abt whitelist"
date: 2011-03-17
forum: Networking &amp; Wireless
---

### Post by phuonghanu on 2011-03-17
Hi all,
 I just send this message to you to ask about one problem that I have  to solve now. I have a database of email in my linux virtual machine.  this table includes some fiedls such as ID, Spam, Data, Time,  Sender_add, sender_ip, sender_domain,&#8230;.


 since I do a project on automatic whitelist so the data preprocessing  is very important. My problem is that i still dont know how to generate  a database for my whitelist from that database because one domain can  include many IP addresses. My job is to group them all (by a script  maybe).


 For example: gmail.com: 38.98.127.148, 74.125.46.29, 74.125.46.30, &#8230;..


 From those pair of IP-domain, I have to find threshold to figure out  which IP is used for sending spam. threshold can be "3 days" (for  example) because spammers will just use IP to spread spams in such a  short time. after removing the illegal IP, we have final whitelist to  apply in email sys


 so what i just want to care abt are sender_ip, and sender_domain. And  when I use mySQL command to list out the number of rows in the table,  the result is more than 46,000 rows >.< (SELECT sender_ip,  sender_domain FROM emailsl;) &#8212;-> i can not do it manually by see each  line and note down the paper "what domain" has "what IP"


 That why i just ask u for method to solve this pre-problem. This step  in data preprocessing is very important because it creats the DB for my  whitelist in any email sys.


 What i'm having: email db, linux virtual machine, mySQL


 What i want: build db in which show the pairs of sender domain-legal IP (cross out illegal IPs and domains based on the threshold)


 Hope u see my point and help me abt that

---

### Post by koszta on 2011-03-17
I am really not sure if I got you right.... if I understood you are trying to obtain a SQL command that would help you to retrieve all IPs for a certain domain from your table ? 

sql > SELECT ip, domain FROM table GROUP BY domain

... you can also write a function to CONCAT IPs together for a single domain (this should be rather done in a programming language like perl or php than using a database stored procedure). 

it should be something like 
#!/usr/bin/perl
my $q= new DBI;
@field_of_IPs= $q->select( SELECT ip, domain FROM table GROUP BY domain);
my $currdomain=$field_of_IPs[0][1]; 
my $currstring=undef;
foreach my $ip (@field_of_IPs) {
if ($curdomain == $ip[1]) {
$currstring.=.':::'.$ip[0];
}
else {
print 'IPs for domain'.$currdomain."\n";
print $currstring;
 $currstring=undef;
$currdomain=ip[1];
}

}

---

### Post by phuonghanu on 2011-03-17
First of all, thanks for ur reply,koszta ^^

I just want to generate a db for my whitelist. After grouping the IPs and domain, I have to find out the threshold to remove the illegal IPs (which used to send spams in the email system). It's not just as simple as obtain an SQL command actually.

My whitelist db stores the info abt a domain and its lega IP addresses. Each record have to contains two data fields: first field is domain and the second one keeps a list of IP addresses that belong to that domain.

there are 2 ways to build up db:

1. contact with domain names owners, asking for the IP addresses of each domain name --> impossible mission ^^

2. build db based on the info extracted fr email header ---> maybe I have to **implement a script to extract needed info in email header from my email db**

i also have to **find out the Active Duration of all pairs of domain-IP**. the active duration (in days) of one pair is indicated from the first time to the last time sending mail event occurs. as u know, spam servers used to send many spams just in a short time. For example, spam servers just send out spam in the period of less than 5 days, so 5 days can be used as threshold in recognizing the illegal IP, domains ---> this info can be used to authenticate one sender, and generate whitelist db. ---> based on email db, i have to **extract info abt Active duration of all pairs of domain-IP addresses**

In general, we extract info about domain name, ip addresses, and active duration to list out the domain-its legal IP ---> my whitelist!

hope u see my point ^^ sighh, sometimes i find it hard to describe what i want to say

---

### Post by gzarkadas on 2011-03-17
In order to exclude spam based on threshold you will need additional fields in your query (most probably the Time field you mentioned in your post). 

An "ideal" sample query (untested of course) is listed below. You will have to adjust it to the specific sql dialect that your database uses.

```

SELECT sender_ip, sender_domain, max(time)-min(time) as duration 
FROM emails
WHERE duration > threshold
GROUPBY sender_domain, sender_ip
ORDERBY sender_domain, sender_ip, duration 

```Pay attention to the units of time; you may need to scale your threshold accordingly (for example if time is given with second accuracy, then duration will be in seconds and that means that if threshold is 5 days, you 'll have to supply 5*24*3600 as "threshold" in your query.

---

### Post by phuonghanu on 2011-03-18
again, i think it's not mySQL command problem.

thing that i want to dig in is the script (or the method) to creat my whitelist based on the email db. the list will contain pairs domain-its legal IPs

I'd use this list together with the plugin to prevent spam in my email sys.

hope to see ur response asap ^^

---

