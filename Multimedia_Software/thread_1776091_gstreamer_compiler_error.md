---
title: "gstreamer compiler error"
date: 2011-06-05
forum: Multimedia Software
---

### Post by zahidul_haque on 2011-06-05
Hi All,

I am new to UBUNTU. I installed Ubuntu10.10 and tried running the gstreamer example.
I wrote simple gstreamer example with C flavour only like

#include <gst/gst.h>
#include <glib.h>

int main() {
    g_print("Hello! World \n");
}

but I am getting compiler error "streamer.c:1: fatal error: gst/gst.h: No such file or directory
compilation terminated."

These header files are at

[B]/usr/include/glib-2.0/glib.h
[/B]
**/usr/include/****gstreamer-0.10/gst/gst.h**

Does anyone has an idea how to resolve this. Thanks in advance

Regards,
Zahid

---

### Post by zahidul_haque on 2011-06-09
any way solved it
**gcc -Wall       $(pkg-config --cflags --libs gstreamer-0.10)       helloworld.c -o helloworld**

---

### Post by vrfriend on 2011-11-15
[FONT=Arial]Hi 
I am new to gstreamer and also ubuntu ......
i am trying to compile my Helloworld.c program but i am getting the following error


r22@cp1:~/Desktop$ gcc -Wall $(pkg-config --cflags --libs gstreamer-0.11) Helloworld.c -o helloworld[/FONT]  [FONT=Arial]

In file included from Helloworld.c:2:0:[/FONT] [FONT=Arial]
/usr/local/include/gstreamer-0.11/gst/gst.h:28:2: warning: #warning "The GStreamer 0.11 API is still unstable and will change in future." [-Wcpp]
/usr/local/include/gstreamer-0.11/gst/gst.h:29:2: warning: #warning "Define GST_USE_UNSTABLE_API to avoid this warning." [-Wcpp]
/tmp/ccVtYDmM.o: In function `bus_call':
Helloworld.c:(.text+0x26): undefined reference to `g_print'
Helloworld.c:(.text+0x31): undefined reference to `g_main_loop_quit'
Helloworld.c:(.text+0x4c): undefined reference to `gst_message_parse_error'
Helloworld.c:(.text+0x57): undefined reference to `g_free'
Helloworld.c:(.text+0x6d): undefined reference to `g_printerr'
Helloworld.c:(.text+0x78): undefined reference to `g_error_free'
Helloworld.c:(.text+0x83): undefined reference to `g_main_loop_quit'
/tmp/ccVtYDmM.o: In function `on_pad_added':
Helloworld.c:(.text+0xa5): undefined reference to `g_print'
Helloworld.c:(.text+0xb8): undefined reference to `gst_element_get_static_pad'
Helloworld.c:(.text+0xcd): undefined reference to `gst_pad_link'
Helloworld.c:(.text+0xd8): undefined reference to `gst_object_unref'
/tmp/ccVtYDmM.o: In function `main':
Helloworld.c:(.text+0xf6): undefined reference to `gst_init'
Helloworld.c:(.text+0x10a): undefined reference to `g_main_loop_new'
Helloworld.c:(.text+0x12b): undefined reference to `g_printerr'
Helloworld.c:(.text+0x141): undefined reference to `gst_pipeline_new'
Helloworld.c:(.text+0x159): undefined reference to `gst_element_factory_make'
Helloworld.c:(.text+0x171): undefined reference to `gst_element_factory_make'
Helloworld.c:(.text+0x189): undefined reference to `gst_element_factory_make'
Helloworld.c:(.text+0x1a1): undefined reference to `gst_element_factory_make'
Helloworld.c:(.text+0x1b9): undefined reference to `gst_element_factory_make'
Helloworld.c:(.text+0x1f3): undefined reference to `g_printerr'
Helloworld.c:(.text+0x219): undefined reference to `g_type_check_instance_cast'
Helloworld.c:(.text+0x235): undefined reference to `g_object_set'
Helloworld.c:(.text+0x23a): undefined reference to `gst_pipeline_get_type'
Helloworld.c:(.text+0x24a): undefined reference to `g_type_check_instance_cast'
Helloworld.c:(.text+0x252): undefined reference to `gst_pipeline_get_bus'
Helloworld.c:(.text+0x272): undefined reference to `gst_bus_add_watch'
Helloworld.c:(.text+0x27e): undefined reference to `gst_object_unref'
Helloworld.c:(.text+0x283): undefined reference to `gst_bin_get_type'
Helloworld.c:(.text+0x293): undefined reference to `g_type_check_instance_cast'
Helloworld.c:(.text+0x2cb): undefined reference to `gst_bin_add_many'
Helloworld.c:(.text+0x2df): undefined reference to `gst_element_link'
Helloworld.c:(.text+0x303): undefined reference to `gst_element_link_many'
Helloworld.c:(.text+0x338): undefined reference to `g_signal_connect_data'
Helloworld.c:(.text+0x350): undefined reference to `g_print'
Helloworld.c:(.text+0x364): undefined reference to `gst_element_set_state'
Helloworld.c:(.text+0x370): undefined reference to `g_print'
Helloworld.c:(.text+0x37c): undefined reference to `g_main_loop_run'
Helloworld.c:(.text+0x388): undefined reference to `g_print'
Helloworld.c:(.text+0x39c): undefined reference to `gst_element_set_state'
Helloworld.c:(.text+0x3a8): undefined reference to `g_print'
Helloworld.c:(.text+0x3ad): undefined reference to `gst_object_get_type'
Helloworld.c:(.text+0x3bd): undefined reference to `g_type_check_instance_cast'
Helloworld.c:(.text+0x3c5): undefined reference to `gst_object_unref'
collect2: ld returned 1 exit status

can anyone help me to sort out this prob.....[/FONT] [FONT=Arial]
i have set the PKG_CONFIG_PATH to /usr/local/lib/pkgconfig
as it is the default path.

Waiting for your help[/FONT]

---

