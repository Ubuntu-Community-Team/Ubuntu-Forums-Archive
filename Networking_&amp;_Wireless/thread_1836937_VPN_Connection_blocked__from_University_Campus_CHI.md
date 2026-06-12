---
title: "VPN Connection blocked  from University Campus CHINA"
date: 2011-08-31
forum: Networking &amp; Wireless
---

### Post by steveninchina on 2011-08-31
Hi All !

i just subscribed from PureVPN. I can not connect from VPN (The PPTP connection failed)- wifi and Eth0.

I am in University campus in China, I'm connect through the university network ( School username & P.W). Blocked by Campus router or bad Network panel configuration ? I am lost (i am dummy).

My OS is UBUNTU 10.04, PPTP connection.


The following commands return me back to the GOOGLE search Engine :

telnet us2.purevpn.net 1701

and

telnet us2.purevpn.net 1723


How to set-up the ADVANCED parameters (PPTP ADVANCED OPTIONS) ?


The previously proposed solutions here, do not work on my machine. Any suggestions ??

Thanks for your help !

Steven.

---

### Post by steveninchina on 2011-09-01
i used to set-up the VPN connection via Ubuntu NETWORK MANAGER. I also used Ubuntu NETWORK TOOLS, and this is some informations:

- I'am able to ping the VPN server adress.
- Traceroute : I reached the Campus IP adress.
- PORT SCAN : 3 ports are open (Campus IP), 1316, 39755, 56964.

...

---

### Post by praseodym on 2011-09-01
Hi,

does the VPN-server use LZO-compression? If so you have to actvate it also in the network-manager-applet (advanced settings)

---

### Post by northd_tech on 2011-09-01
I'm not sure if this is part of your problem (or what you are wanting to work around), but I do know that China censors much of the internet.

These articles discuss that:

**The Great Firewall of China: Internet Companies Censor Material at Chinese Government’s Request**
> We take a look at why the internet company Google is coming under intense criticism for agreeing to censor material deemed objectionable by the Chinese government and how Yahoo and Microsoft comply with China’s censorship orders. And in the U.S., the internet companies have provided the government with information on users at the Justice Department’s request. We speak with UC Berkeley school of law professor Deirdre Mulligan about the issue of telecom companies working with governments.
[http://www.democracynow.org/2006/1/27/the_great_firewall_of_china_internet](http://www.democracynow.org/2006/1/27/the_great_firewall_of_china_internet)

What Does China Censor Online?
Censored Keywords and Websites
[http://www.informationisbeautiful.net/2010/what-does-china-censor-online/](http://www.informationisbeautiful.net/2010/what-does-china-censor-online/)

Empirical Analysis of Internet Filtering in China

Jonathan Zittrain* and Benjamin Edelman**
Berkman Center for Internet & Society
Harvard Law School
[http://cyber.law.harvard.edu/filtering/china/](http://cyber.law.harvard.edu/filtering/china/)

Google censors itself for China 
> Leading internet company Google has said it will censor its search services in China in order to gain greater access to China's fast-growing market.

Google has offered a Chinese-language version of its search engine for years but users have been frustrated by government blocks on the site.

The company is setting up a new site - Google.cn - which it will censor itself to satisfy the authorities in Beijing.

Google argued it would be more damaging to pull out of China altogether. 

Critics warn the new version could restrict access to thousands of sensitive terms and web sites. Such topics are likely to include independence for Taiwan and the 1989 Tiananmen Square massacre.

The Chinese government keeps a tight rein on the internet and what users can access. The BBC news site is inaccessible, while a search on Google.cn for the banned Falun Gong spiritual movement directs users to a string of condemnatory articles.

Google's move in China comes less than a week after it resisted efforts by the US Department of Justice to make it disclose data on what people were searching for. 

Google hopes its new address will make the search engine easier to use and quicker.

Its e-mail, chat room and blogging services will not be available because of concerns the government could demand users' personal information.

Google said it planned to notify users when access had been restricted on certain search terms.

The company argues it can play a more useful role in China by participating than by boycotting it, despite the compromises involved.

"While removing search results is inconsistent with Google's mission, providing no information (or a heavily degraded user experience that amounts to no information) is more inconsistent with our mission," a statement said. 

Julian Pain, internet spokesman for campaign group Reporters Without Borders, said Google's decision to "collaborate" with the Chinese government was "a real shame".

The number of internet search users in China is predicted to increase from about 100 million currently to 187 million in two years' time.

A survey last August revealed Google was losing market share to Beijing-based rival Baidu.com.

Last year, Yahoo was accused of supplying data to China that was used as evidence to jail a Chinese journalist for 10 years. 

[http://news.bbc.co.uk/2/hi/technology/4645596.stm](http://news.bbc.co.uk/2/hi/technology/4645596.stm)

Internet censorship in the People's Republic of China
[http://en.wikipedia.org/wiki/Internet_censorship_in_the_People%27s_Republic_of_China](http://en.wikipedia.org/wiki/Internet_censorship_in_the_People%27s_Republic_of_China)

---

### Post by northd_tech on 2011-09-01
> **steveninchina said:**
> 
- Traceroute : I reached the Campus IP adress.


I'm curious here- what results do the following terminal commands give you there in China?

```
traceroute www.google.com
traceroute www.ucla.edu
traceroute www.crayola.com
traceroute www.msn.com
traceroute www.bbc.com

```

---

