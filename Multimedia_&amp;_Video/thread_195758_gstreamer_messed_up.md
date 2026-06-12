---
title: "gstreamer messed up"
date: 2006-06-13
forum: Multimedia &amp; Video
---

### Post by pashby on 2006-06-13
Hi 

Unfortunately I have messed up my installation of gstreamer. A result of this is that I can't use the media player 'Listen'. I can however use Amarok.

Whenever I try to start Listen I get this message

peter@ubuntu:~/sw/gstreamer-0.10.8$ listen
ERROR (0x81aead0 - 0:00:01.457352000)         GST_PIPELINE( 6790) ./grammar.y(578):_gst_parse__yyparse: no element "gconfaudiosink"
ERROR (0x81aead0 - 0:00:01.457733000)         GST_PIPELINE( 6790) ./grammar.y(837):_gst_parse_launch: Unrecoverable syntax error while parsing pipeline gconfaudiosink
ERROR (0x81aead0 - 0:00:01.493908000)         GST_PIPELINE( 6790) ./grammar.y(578):_gst_parse__yyparse: no element "xvimagesink"
ERROR (0x81aead0 - 0:00:01.494119000)         GST_PIPELINE( 6790) ./grammar.y(837):_gst_parse_launch: Unrecoverable syntax error while parsing pipeline xvimagesink
Element xvimagesink not found for Gstreamer, visualisation disable

I have tried removing and reinstalling gstreamer and have compiled from source but always this message appers and Listen freezes.

Can someone please help.

Thanks Peter

---

