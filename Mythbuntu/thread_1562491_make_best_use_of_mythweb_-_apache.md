---
title: "make best use of mythweb - apache"
date: 2010-08-27
forum: Mythbuntu
---

### Post by geekyhawkes on 2010-08-27
hello;

i have an ip webcam and my myth box behind the same router, that sadly doesnt support several port forwards ( from what i can see anyway), so i was wondering if i could get mythweb to forward me via a link to the ip cam if i wanted it?

I was also wondering if i could use my machine to get around the firewall at work?  I can access my myth box from work and was thinking i could use it to get at other parts of the internet that are blocked (like google calander etc)

Thanks

---

### Post by ian dobson on 2010-08-28
Hi,

I think the only way to get your webcam accessable over the internet would be to use a cgi script that runs on your mythbackend server, grabs the image from your camera and dumps it to the client. Abit like a proxy.

Something like:-
```
#!/usr/bin/perl --

  # Create a user agent object
  use LWP::UserAgent;
  $ua = new LWP::UserAgent;
  $ua->agent("AgentName/0.1 " . $ua->agent);
  # Create a request
  my $req = new HTTP::Request GET => 'http://link_to_your_ip_camera_image';
  $req->content_type('Accept: image/jpeg');
  $req->content_type('Connection: Keep-Alive');
  my $res = $ua->request($req);
  # Check the outcome of the response
  if ($res->is_success) {
  	  binmode stdout;
	  print "Content-type: image/jpeg\n\n"; 
      print $res->content;
  } else {
      print "Bad luck this time\n";
  }


exit;
```
Regards
Ian Dobson

---

### Post by DemonBob on 2010-08-28
> **geekyhawkes said:**
> 
I was also wondering if i could use my machine to get around the firewall at work?  I can access my myth box from work and was thinking i could use it to get at other parts of the internet that are blocked (like google calander etc)

Thanks

For the second part, we are not going to help you circumvent your company security policies so you can browse the internet. I am the IT Manager for my company, and have fired quite a few people because of stuff like this. The policies, and blocks are there for a reason.

---

### Post by scottishnarn on 2010-08-28
You can use mod_proxy to accomplish what you want with your webcam.  See [http://httpd.apache.org/docs/2.2/mod/mod_proxy.html](http://httpd.apache.org/docs/2.2/mod/mod_proxy.html) If you want more details just ask.

---

### Post by geekyhawkes on 2010-08-30
Ok, Im working at the limit of my knowledge here, can i get a bit of help with the mod_proxy please.

My setup is;

Mythbox on fixed IP (192.168.1.11) with mythweb running.  I am using NAT to get access to mythweb from outside my home network.  (This works currently)

The webcam is on another apache server (for what thats worth) running on a nokia N800, it is controlled by a very simple webpage that is available at the ip address of the n800/webcam.html.

I want to have the option to access this page (and googlecalender would be nice as this is blocked with the work firewall for no good reason) via my mythweb front page (or at least the apache server on my myth box).

I guess the other option could be to create a pretty simple home page on my own myth machine with links to mythweb and webcam? 

Thanks for the help, I really want to maximise the use of my myth machine now i have the tv / media side largely setup!

---

### Post by geekyhawkes on 2010-09-01
Anyone able to offer me some more help on this mod_proxy setting?

---

### Post by ian dobson on 2010-09-01
Hi,

I don't think you'll get a great deal of help here for mod_proxy, as you want to miss use it to get around limitations applied by your employer. Google abit and you'll find the answers your looking for. 

This forum is for Mythbuntu/MythTV.

Regards
Ian Dobson

---

### Post by scottishnarn on 2010-09-01
While I had this setup with an earlier version of Ubuntu I've been trying to replicate it with the latest edition and I'm having a little trouble. I'll post something when I get it to work. (the webcam bit) But this isn't really a mythbuntu issue, it's an apache issue. So you might have better luck posting to a different forum.

---

