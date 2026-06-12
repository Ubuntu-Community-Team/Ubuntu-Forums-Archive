---
title: "Cannot connetct IDJC to Shoutcast server on my web server"
date: 2011-01-26
forum: Multimedia Software
---

### Post by jackopo on 2011-01-26
Hi Folks,

I'm looking for help.

I'm trying to connect idjc to a shoutcast server which is running on a web server (i'm not trying to use a local instance of shoutcast), while idjc is running on my computer.

In the sc_serv.conf file as SrcIP I use ANY, cause I thought I was trying to access the server from another machine.


idjc gives me this output (in a terminal) when I try to connect with the web server:

```
encoder_start: resampler will not be used
encoder_start: successfully started the encoder
live_mp3_build_metadata: metadata for encoder 0
metadata=
streamer_connect: established connection to the server
streamer_main: busy, waiting for the server to grant access
streamer_main: busy, waiting for the server to grant access
encoder 0 running
streamer_main: busy, waiting for the server to grant access
streamer_main: busy, waiting for the server to grant access
encoder 0 running
streamer_main: busy, waiting for the server to grant access
streamer_main: busy, waiting for the server to grant access
streamer_main: connection failed, shout_get_error reports -4 No error
streamer_main: disconencting from server
encoder_unregister_client called
encoder_unregister_client finished
streamer_main: disconnection complete
streamer_disconnect: function called while not streaming
command failed for command: server_disconnect
encoder_plugin_terminate: waiting for encoder to finish
live_mp3_encoder_main: flushing 583 bytes
live_mp3_encoder_main: performing cleanup
live_mp3_encoder_main: finished cleanup
encoder_stop: encoder is stopped

```

The Shoutcast server seems running to me.

I don't know, does anyone have a clue about it?

Thanks a lot for your help :)

PS sorry my english is not that good

---

### Post by StephenF on 2011-01-26
Shoutcast 2 is not supported. Post the Shoutcast log for more assistance.

---

