---
title: "unable to play gstreamer in QWidget"
date: 2014-01-30
forum: Multimedia Software
---

### Post by prkhr4u on 2014-01-30
I am trying to use gstreamer to play video from a network camera in QWidget.
I am utilizing "mjpeg" stream of the camera.

I am able to successfully play the video in terminal using :
```
gst-launch souphttpsrc location=http://169.254.75.39/video2.mjpg timeout=5 ! jpegdec ! xvimagesink
```

The same code I am trying to play in QWidget using this code:
```
#include <glib.h>
#include <gst/gst.h>
#include <gst/interfaces/xoverlay.h>

#include <QApplication>
#include <QTimer>
#include <QWidget>

int main(int argc, char *argv[])
{
  if (!g_thread_supported ())
    g_thread_init (NULL);

  gst_init (&argc, &argv);
  QApplication app(argc, argv);
  app.connect(&app, SIGNAL(lastWindowClosed()), &app, SLOT(quit ()));

  // prepare the pipeline

  GstElement *pipeline = gst_pipeline_new ("xvoverlay");
  GstElement *src = gst_element_factory_make ("souphttpsrc",NULL);
  GstElement *sink = gst_element_factory_make ("xvimagesink", NULL);
  gst_bin_add_many (GST_BIN (pipeline), src, sink, NULL);
  gst_element_link (src, sink);
  g_object_set (src, "location", "http://169.254.75.39/video2.mjpg", NULL);
  // prepare the ui

  QWidget window;
  window.move(0,0);
  window.resize(320, 240);
  window.show();

  WId xwinid = window.winId();
  gst_x_overlay_set_window_handle (GST_X_OVERLAY (sink), xwinid);

  // run the pipeline

  GstStateChangeReturn sret = gst_element_set_state (pipeline,
      GST_STATE_PLAYING);
  if (sret == GST_STATE_CHANGE_FAILURE) {
    gst_element_set_state (pipeline, GST_STATE_NULL);
    gst_object_unref (pipeline);
    // Exit application
    QTimer::singleShot(0, QApplication::activeWindow(), SLOT(quit()));
  }

  int ret = app.exec();

  window.hide();
  gst_element_set_state (pipeline, GST_STATE_NULL);
  gst_object_unref (pipeline);

  return ret;
}

```

When I run the code,all I am getting is a blank QWidget with nothing.

My gstreamer has been correctly setup in QT and I was able to play a sample pattern easily in QWidget.

I guess I am missing the decoder configuration in QT for 'jpegdec'
Can anyone tell how to correctly set it up?
Here is the .pro file content:
```
QT       += core gui

TARGET = streaming
TEMPLATE = app


SOURCES += main.cpp\
        mainwindow.cpp

HEADERS  += mainwindow.h

FORMS    += mainwindow.ui

CONFIG += link_pkgconfig
PKGCONFIG += gstreamer-0.10\
gstreamer-interfaces-0.10\
gtk+-2.0\

QMAKE_CXXFLAGS += -fpermissive
```

P.S. : using ubuntu 12.04

---

