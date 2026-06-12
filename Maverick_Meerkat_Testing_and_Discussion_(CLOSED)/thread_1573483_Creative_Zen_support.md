---
title: "Creative Zen support"
date: 2010-09-12
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by eddier on 2010-09-12
I see that Gnomad has been dropped and Creative zen x-fi is now usable as a device and music folders can be dragged and dropped.  nice one!

eddie

---

### Post by eddier on 2010-09-20
Well I dont know whats happened but its foobarred again,looks like libmtp is the culprit-possibly.

```
eddie@eddie-desktop:~$ rhythmbox

(rhythmbox:17822): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
** Message: pygobject_register_sinkfunc is deprecated (GstObject)
** (rhythmbox:17822): DEBUG: SyncDaemon already running, initializing SyncdaemonDaemon object
Traceback (most recent call last):
  File "/usr/lib/rhythmbox/plugins/umusicstore/__init__.py", line 49, in activate
    shell.props.sourcelist.select(self.source)
AttributeError: 'U1MusicStorePlugin' object has no attribute 'source'
** (rhythmbox:17822): DEBUG: Loading the real store page

** (rhythmbox:17822): WARNING **: Got less number of items in credentials hash table than expected!
** (rhythmbox:17822): DEBUG: navigation requested to https://one.ubuntu.com/music/store-no-token
Device 0 (VID=041e and PID=4162) is a Creative ZEN X-Fi.
Device 0 (VID=041e and PID=4162) is a Creative ZEN X-Fi.
Device 0 (VID=041e and PID=4162) is a Creative ZEN X-Fi.
Device 0 (VID=041e and PID=4162) is a Creative ZEN X-Fi.
Device 0 (VID=041e and PID=4162) is a Creative ZEN X-Fi.
ignoring usb_claim_interface = -16ignoring usb_claim_interface = -22PTP_ERROR_IO: Trying again after re-initializing USB interface
inep: usb_get_endpoint_status(): Device or resource busy
outep: usb_get_endpoint_status(): Device or resource busy
usb_clear_halt() on IN endpoint: Device or resource busy
usb_clear_halt() on OUT endpoint: Device or resource busy
usb_clear_halt() on INTERRUPT endpoint: Device or resource busy
ignoring usb_claim_interface = -16ignoring usb_claim_interface = -22LIBMTP PANIC: Could not open session! (Return code 767)
  Try to reset the device.

(rhythmbox:17822): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `<invalid>'

(rhythmbox:17822): GLib-GObject-CRITICAL **: g_signal_handlers_unblock_matched: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(rhythmbox:17822): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `<invalid>'

(rhythmbox:17822): GLib-GObject-CRITICAL **: g_signal_handlers_unblock_matched: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(rhythmbox:17822): Rhythmbox-CRITICAL **: rb_property_view_set_selection: assertion `RB_IS_PROPERTY_VIEW (view)' failed

(rhythmbox:17822): GLib-GObject-WARNING **: instance with invalid (NULL) class pointer

(rhythmbox:17822): GLib-GObject-CRITICAL **: g_signal_handlers_unblock_matched: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(rhythmbox:17822): GLib-GObject-WARNING **: instance with invalid (NULL) class pointer

(rhythmbox:17822): GLib-GObject-CRITICAL **: g_signal_handlers_unblock_matched: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(rhythmbox:17822): Rhythmbox-CRITICAL **: rb_property_view_set_selection: assertion `RB_IS_PROPERTY_VIEW (view)' failed
** (rhythmbox:17822): DEBUG: navigation requested to http://stores.7digital.com/default.aspx?shop=34&partner=983

(rhythmbox:17822): Rhythmbox-WARNING **: libmtp error: PTP Layer error 2002: get_handles_recursively(): could not get object handles.

(rhythmbox:17822): Rhythmbox-WARNING **: libmtp error: (Look this up in ptp.h for an explanation.)


```


Anyone see a way round this ?

I notice Gnomad2 is missing from the M.M. repo's.

eddie

---

### Post by eddier on 2010-09-20
Further to the above. Trying to open device as a folder gives the following,

"Could not display "gphoto2://[usb:001,004]/:""


eddie

---

