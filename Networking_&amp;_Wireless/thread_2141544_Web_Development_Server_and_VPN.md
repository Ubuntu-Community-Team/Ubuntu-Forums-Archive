---
title: "Web Development Server and VPN"
date: 2013-05-03
forum: Networking &amp; Wireless
---

### Post by pjm2008 on 2013-05-03
So, right now I'm working on getting my second Ubuntu Server up. This time I'm looking to make it a dedicated web development server. I know how to set this up for local development on my home network. 


Though I want to setup a VPN. The idea behind this is to allow me to connect to my network back home. The VPN I am looking to setup is to use OpenVPN. This would run on my server. The idea would allow me to connect to my home network securely of course. Then it would allow me to test my web app from an outside connection without having to worry about setting up local URLs in my dev environment. Also this would allow me to have consistent access to my databases, server side processing, etc. 

One question I have is there any pitfall I may face or something to pay attention to when setting up the VPN so I do not get in the way of my locally hosted web server calls? I understand that VPN and a Web Server usually listens on 80, should I change the VPN to listen on a different port? If so, would this cause any problems with then directing my computer I am using outside the network when I do localhost in the web browser to view my web app? 

My next question is this the best method for multiple members to have a good development server to be able to test the app? 

Then lastly, I'm having troubles finding any tutorials for good setups for development servers. I just want my members to be able to connect to my local network to have consistent calls in their development environments for the services we need to test. 

Any information would be great. Thank you.

---

### Post by ahallubuntu on 2013-05-03
~

---

### Post by pjm2008 on 2013-05-03
So, right now I am using my own computer to do my web development. So when I check my website, I call localhost. Though when I am not on my network, such as at school or else where, they could have their network configured so that localhost points to another machine, so I have to figure out what my hostname is on that network and change my local URL in my dev environment. I use Coda which saves local URL base root so that it knows where to look for content. I then have my Apache of course pointing to my localhost. 

So what I am doing is developing a website using MongoDB and Node.js. I am trying to make it so where a collection of developers have access to the same database and able to write server side requests as well. 

I'm trying to get it so we have a consistent environment for testing our web app for development outside a local network but are able to work with the database and server side scripting.

EDIT: And yes I can open that port. I didn't realize it. I'm just reading through the OpenVPN documentation.

---

