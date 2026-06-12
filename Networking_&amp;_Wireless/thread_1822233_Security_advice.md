---
title: "Security advice"
date: 2011-08-10
forum: Networking &amp; Wireless
---

### Post by jon.mithe on 2011-08-10
Hi,

I'm a dev with a fair amount of experience in ubuntu but not that much with systems. I have a dev environment at home that I would like to secure / tighten down, but I am stuck as to the best strategy.

Server wise, its a single ubuntu box and it hosts git, svn, artifactory / maven repo, hudson build server, trac and a pdf printer, mostly over HTTP or now HTTPS

I dev + build various app's from home on my desktop PC using this server, i.e. my dev env is a seperate server.

My problem is I am on a generally unsecure wireless network which is also shared by 3 other people and soon to be another developer / I.T literate person who I do not know (and therefore do not trust for now).

I've been playing and have set up my dev tools over HTTPS and using htaccess.  This "works" (everything seems secure), but is causing me all sorts of issues developing.  Primarliy maven is not working / auth is proving difficult.  I've solved the issue of self certified certificates, but auth it proving a nightmare, and at best I have to store a user name / password in plain text.  I havnt got hudson and git working together yet, its easy with HTTP but I think the auth is going to provide more problems (hmmm, could probably do some localhost http to solve that)

I'm thinking this is silly trying to secure eveything independantly (so many random technologies) -- and maybe a better way is to create some sort of VPN and run everything over http / simple setup.  But this is where my expertise run out.  I hear there is an issue with DNS.

Is there a better way to do this?  Anyone give any advice about what steps to take with VPN.  The machine I dev on is ubuntu, but I do have a windows box which I'd like to at least have the possibility of connecting.

The only other strategy is to buy some sort of router / firewall and set up my own secure local network.  Although this seems like the best solution, I'm thinking its a little overkill and is ultimately going to be more painful.

I'm thinking a VPN is the way forward?  I like the idea of being able to ssh into my box externally and setting up a VPN to gain access to my dev environment.

Thanks for any help, getting a little stuck :/
Jon

---

