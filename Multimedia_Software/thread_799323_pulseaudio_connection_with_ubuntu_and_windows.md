---
title: "pulseaudio connection with ubuntu and windows"
date: 2008-05-18
forum: Multimedia Software
---

### Post by AliTabuger7 on 2008-05-18
I am using Ubuntu 8.04 and Vista Home Premium.

After working on this for so long, the terminology is becoming very confusing.

What I'm hoping to do is stream whatever sound is coming from my Vista computer to my Ubuntu computer where it will be played over the speakers.

Pulseaudio is supposed to be designed to do such a thing. The windows version apparently does not have RTP, which i believe is necessary to do this.

The Pulseaudio FAQ suggests very different ways of doing this:

> How can use my Windows box to play the sound from my Linux box?

    * Download the windows binary of pulseaudio from the download page.
    * In the pulseaudio directory, create a file default.pa whith a content similar to this one (you may have to adjust the auth-ip-acl to reflect your network's settings):

      load-module module-waveout

      load-module module-native-protocol-tcp auth-ip-acl=127.0.0.1;192.168.0.0/16

    * In pulseaudio applet: PA applet -> Default Server -> Other -> Enter the hostname or ip of your windows box. 
The suggestion above I believe is the opposite of what I'm looking for. I need it to go from Windows to Ubuntu.

The problem with the suggestion below is that I cannot get RTP to work on windows. I keep on getting failed to load module module-rtp-send.
> How can I use PulseAudio to stream music from my main PC to my LAN with multiple PCs with speakers?

    On the sender side create an RTP sink:

    load-module module-null-sink sink_name=rtp
    load-module module-rtp-send source=rtp.monitor
    set-default-sink rtp

    This will make rtp the default sink, i.e. all applications will write to this virtual RTP device by default.
    On the client sides just load the reciever module:

    load-module module-rtp-recv

    Now you can play your favourite music on the sender side and all clients will output it simultaneously.
    BTW: You can have more than one sender machine set up like this. The audio data will be mixed on the client side.

If there is no way to get PulseAudio to work, I tried looking up some alternatives. Jack Audio is supposed be available on windows soon. There is also some kind of ESD driver for windows, but that is in really early alpha and is not maintained.

Any help, suggestions, or alternatives are greatly appreciated.

---

### Post by AliTabuger7 on 2008-05-23
The more I look at it, Icecast may be a viable alternative, if I can figure out how to get it to relay all of the sounds made, instead of if using a queue of files.

---

### Post by AliTabuger7 on 2008-05-25
As an update, there are some complicated ways of getting this to work. In case this is searched for later, here they are.

Pro: This will work with any audio played on windows.

Con: there is about 4-5 seconds of delay between the sounds on the server and the sounds on the player. There is not a configuration that I can come up with to alter this, and modifying the buffer on the player does not have a significant impact. All this despite it being on 100 mbps LAN. That being said, it is still possible to increase the bitrate without a noticeable increase in the latency.

1. Get Icecast.

2. Get Edcast

3. Configure edcast to use the output sound instead of the inputs like microphones. This is called "What U Hear" with Creative cards, and called "Stereo Mix" in Realtek cards. 
*If you are using Vista, you will need to enable it. I found [this post]("http://www.driverheaven.net/audio-general-technical-discussion/130879-windows-vista-recoding-what-you-hear-how.html") to be very helpful. ([http://www.driverheaven.net/audio-general-technical-discussion/130879-windows-vista-recoding-what-you-hear-how.html](http://www.driverheaven.net/audio-general-technical-discussion/130879-windows-vista-recoding-what-you-hear-how.html))

4. Add the encoder of your choice and configure it to fit your bandwidth and listening needs.

5. Start the Icecast server (to make reusing easier, check start server on application startup)

6. Connect edcast (to make reusing easier, check autoconnect) To reconnect later, repeat steps 5 and 6.

If anyone knows how to decrease that latency, this would be the perfect setup.

---

### Post by kotnik on 2009-02-23
Did you manage to make Windows send audio to PulseAudio server after all?

Having similar problem, I found this solution:

[http://gleamynode.net/articles/2228/streaming-audio-from-windows-to-pulseaudio-server](http://gleamynode.net/articles/2228/streaming-audio-from-windows-to-pulseaudio-server)

But I can only send audio from microphone :(

---

### Post by elysion on 2009-03-14
I'm also looking for a solution to this. Tried using Icecast, but the delay was a bit annoying.

Seems that LiveInCode selects the correct source to send to the server when I use the instructions in here: [http://gleamynode.net/articles/2228/streaming-audio-from-windows-to-pulseaudio-server](http://gleamynode.net/articles/2228/streaming-audio-from-windows-to-pulseaudio-server)
Don't get any errors, but don't either get any audio out of the speakers. What do I need to do on the server side? How do I configure the pulseaudio server there to listen to the data being sent from the other PC?

---

### Post by elysion on 2009-03-20
> **kotnik said:**
> Did you manage to make Windows send audio to PulseAudio server after all?

Having similar problem, I found this solution:

[http://gleamynode.net/articles/2228/streaming-audio-from-windows-to-pulseaudio-server](http://gleamynode.net/articles/2228/streaming-audio-from-windows-to-pulseaudio-server)

But I can only send audio from microphone :(

Did you select the source from the recording control in windows? I had the same problem, but that was quite easily fixed by connecting the headphone output to the line in and selecting line in in the recording control.

I get still a ~2s delay, but it's much better than what i got with icecast (~10s). Would still like to get pulseaudio to work, but can't really understand that system and the FAQ in the Wiki is not much help either :/.

---

### Post by markbuntu on 2009-03-20
Nobody has worked on the pulseaudio for windows project for a few years so it has pretty much been abandoned and i don't think the server side was ever really implemented. If there is some other way to set up an rtp server in windows that might be something to try.

---

### Post by markotitel on 2009-06-14
> **kotnik said:**
> Did you manage to make Windows send audio to PulseAudio server after all?

Having similar problem, I found this solution:

[http://gleamynode.net/articles/2228/streaming-audio-from-windows-to-pulseaudio-server](http://gleamynode.net/articles/2228/streaming-audio-from-windows-to-pulseaudio-server)

But I can only send audio from microphone :(

Hi can you please help me, I need only microphone to stream, but cannot get it to work. How did you do it?

---

### Post by jonny-5 on 2009-07-22
Hi. I am having a similar problem. I have icecast2 installed and running on my server. Using nicecast I am able to connect to the server but nicecast only runs on a mac. I am wanting to switch over to ubuntu but I am having a hard time trying to find a nicecast equivalent. 

I am wanting to stream music live over my webiste.

Any help is greatly appreciated!

Thanks

---

