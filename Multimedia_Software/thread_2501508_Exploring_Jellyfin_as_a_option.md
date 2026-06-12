---
title: "Exploring Jellyfin as a option"
date: 2024-10-10
forum: Multimedia Software
---

### Post by sgt-mike on 2024-10-10
[FONT=arial]Like the title states just exploring Jellyfin  as a option.
Currently using plex on old HP 8200 elite ultra SFF .. basically a i7 second gen ([/FONT][COLOR=#010101][FONT=RobotoLocal][FONT=arial] i7-2600S ) with 16 gb ram, no discrete GPU's installed. 
Currently no glaring issues nor really any reason to replacing the current setup. 

But I do plan on shifting a media server into a RV with it's own stand alone network versus relying on internet. 
I know that Plex can be configured to work in this environment. But even so still needs to phone home occasionally. <<< which maybe a problem.

So this leads to the discussion of if Jellyfin will suffice for this in a true stand alone network, as I plan on upgrading the hardware on the current house setup.    
Which doesn't mean if Jellyfin is more to my liking I won't shift from Plex to it for the home media server . which is in the plans for the future, after the NFS is completely online.[/FONT]

[/FONT][/COLOR]

---

### Post by ajgreeny on 2024-10-11
I see no reason why jellyfin would not do what you want.
I tried it for a short time to replace my Emby server setup and for some uses it was excellent. 
However, and for me it was a **big** however, jellyfin will not work for photographs which I need so I moved back again to Emby.
A great shame as I really need a single media-server for all my multimedia files, not a separate one just for photos, and I would much prefer an open source application.

---

### Post by ian-weisser on 2024-10-11
I have used Jellyfin for many years.
The user interface can be a bit rough around the edges when you get deep, but it plays what I want it to play and I have found it very reliable.

---

### Post by tea for one on 2024-10-11
> **ajgreeny said:**
> However, and for me it was a **big** however, jellyfin will not work for photographs which I need so I moved back again to Emby.
According to the Jellyfin documents:-
> You can also add other types of media such as books or photos
[https://jellyfin.org/docs/general/server/libraries/](https://jellyfin.org/docs/general/server/libraries/)

---

### Post by sgt-mike on 2024-10-11
Thanks so far for the replies, I don't expect anyone to provide hard answers for my setup. In order to find that out I just have to try it. But based on the responses so far looks very promising for my objective. Hopefully more folks will weigh in. 

I didn't get into great detail on the TV that I want it to serve to. That is what one if not the driving issue. 
The other is being able to serve the TV in a highly remote area without any internet connection. Plus I want a friendly GUI on the TV showing the coverart, vs a text description. 
 
A Sony Bravia a early version that uses Yahoo TV firmware yeahhhh that is dead venture. I could replace it but it was free.  I could in the past get it to connect to a pure dlna server such as a netgear router or even UMS. My only thing that bothered me was that that TV would never display the cover art or a graphic of the movies with UMS, and render lag to the sony. No matter if I made the coverart available to the server or what. 
Until I plugged a Firestick into it to override /patch the defunct unsupported TV firmware OS. Now I have not tried Plex on the road to see if it would keep a connection to the TV with a cheap netgear router, media server to the TV without internet via a wired connection. I suspect that it could be a issue at some point reconnection wise, maybe. But in it's current configuration It's working great. 

The House TV that is a different story it is a newer LG with it's web OS and it just plain works to my satisfaction with both Plex or UMS, thus far the Plex GUI is way nicer and preferred by the wife and daughter. And I don't have a issue the Plex in it's current setup. I haven't gotten a plex pass to utilize a GPU mainly because the little HP is without a discreet GPU. Not that I couldn't add one. 

I "know" Jellyfin doesn't require a subscription in order to use the GPU hardware such as Plex does. Even though I'm a cheap individual doesn't mean I wouldn't pay for a lifetime pass in order to use it from Plex, or that I'm griping about it. Just currently not doing so with the current server setup doesn't have discrete GPU to assist with encode/decode.  

The other point that has been brought up is the metadata collection with Plex is the one that the Fu has mentioned in other post he has made. It has me wondering if really I should be concerned, which at present it kind of is, but not a deal breaker, yet. 

Photos,,, great point. But not a current concern as I want to just watch ripped movies / tv shows on the road. Could that focus change yep. But from the link provided appears to be able to get it to work.


______________________________

(P.S. I have already downloaded the JellyFin app to the firestick on the Sony TV so that part is ready)

This part below is only for little back ground information of what I'm attempting to achieve with the home lab setup.

This is the auction that I won is the cause to a somewhat of a shift of everything  [https://shopgoodwill.com/item/212043031](https://shopgoodwill.com/item/212043031)

I primarily sought it for it's case for the NFS server, as it has one more external bay than the current case the NFS (or NAS as some will call it) is in. Which my vision was to primarily house the media for the house media server., While also housing other files for various things  software ISO's etc. 

The system I won is on the way now, I truly won't know the hardware specs or if it's even usable until it arrives on Monday. Or if the MB/cpu etc inside is that case more capable than the current little HP. The little HP has always been meant to be a little portable stand alone media server for a RV. 
 
My over all big picture plan involves a lot of case shifting of different systems, as I have never liked the case the Windows 10 box is in which serves a little cheap cnc router mainly, otherwise it would also be a Linux system instead of a Windows environment.

---

### Post by ajgreeny on 2024-10-11
> **tea for one said:**
> According to the Jellyfin documents:-

[https://jellyfin.org/docs/general/server/libraries/](https://jellyfin.org/docs/general/server/libraries/)
Yes I am aware that they say that but having tried it many times I think they do not tell the whole truth as I could not get it to show any photos on my LG Smart TV or any other device so I gave up trying for the current time..

---

### Post by sgt-mike on 2024-10-11
> **ajgreeny said:**
> Yes I am aware that they say that but having tried it many times I think they do not tell the whole truth as I could not get it to show any photos on my LG Smart TV or any other device so I gave up trying for the current time..
Noted thank you, I'll keep your experience in mind, sometimes I change my mind / objective on a whim, and your input might be important to me in the future.

Ohhhh I forgot to mention this part docker ........ not to drift the thread away from Jellyfin. As I really like to stay on topic. 
But as information on the makeup of my hardware right now. While I have used it in other applications that I abandoned, never struck a cord with me. Honestly I didn't give it a chance, stumbled a bit with it, and went on without it. (yeah I know bad Mike .... bad Mike)
As such current systems I have don't use it. 
But that doesn't mean I shouldn't use it once I go to reconfigure, and really don't know if I need to in order to cleanly make use of any discrete GPU's in the future in any media server. But that is another topic unrelated to this.

While I have been filling the pages of this post with background information and reading what some say.  Then going through Jellyfin's recommendations. This part concerns me
 ```
" **Networking[&#8203;]("https://jellyfin.org/docs/general/administration/hardware-selection#networking")**

[FONT=&amp]Networking is for connecting your Jellyfin server to other devices. It is recommended that the server be connected to the internet via Ethernet cables. Wi-Fi or Powerline solutions are NOT recommended. "[/FONT] 

```

hmmm .....  I know what recommended versus required means. But also know that some (developers) like to drive you into their desires not yours. Which can be a problem for the end user. Not really big deal breaker yet, I don't think. In the RV setup I'm not looking to do wireless, but wired without internet. Doesn't mean it won't work but causes a slight pause.

---

### Post by ajgreeny on 2024-10-12
I think their comments about the ethernet recommendation rather than wireless is due to the much greater chance of successful connections with ethernet and similarly the much lower chance of interruptions of the connection than when using wireless devices.

I have both ethernet cable and wireless networks for my Emby (and my Jellyfin when I tried it) on the machines I ue as media servers and both methods worked equally effectively though I admit that I do have excellent and fast wireless here at about 150 M/ps.

If you want to discuss this in more detail I suggest you start another thread as the current title does not explain to where this has now moved.

---

### Post by sgt-mike on 2024-10-13
Yes, 
I sometimes drift sorry. I would mark this thread as solved but just want to see if anyone else has something to say one way or the other on JellyFin good or bad. 
But from all that has replied so far looks like it will work. 
Now does this cause me to ponder hardware. 
Yep but as you advised that if I need to ask hardware wise it should be in a separate thread. Only logical sense to do so.
So to all that has responded thank you so much for your input... 
I'll keep a eye out on this thread for a few days or so then mark it solved in case anyone has any input.


:Updated on 10/17/2024:
After the replies from here I did install Jellyfin on the New Media Server, to replace the HP SFF unit. 
I'm impressed with it as a viable option thus far. I still need to do some things to it to actually get the server to what I want it to do. Which involves HW GPU support, Which I suspect will involve upgrading the GPU to a newer version /models so that the correct nvida driver can kick in and enable the cuda cores. The current GPU's are just too dated. But as far as the thread is concerned the option of JellyFin is a definite go to. Thanks to the few whom answered the post it was greatly appreciated input.

---

