---
title: "Gloobus iMovie Problem"
date: 2009-04-29
forum: Multimedia Software
---

### Post by badchoice on 2009-04-29
Hi,

I'm developing an application, it's called Gloobus and it wants to be a very fast previewer for any kind of file, you can see some screenhots and download it from here:

[http://gloobus.launchpad.net](http://gloobus.launchpad.net)

Now, I can reproduce audio files with gstreamer without any problem, but when I try to do it for movies, they play in his own window.
I've been trying a lot of thing with the xoverlay function that its supposed to be the one to make the video play in a gtk widget but I get an error

If I add the gtk_drawing_area into the GTK_FIXED before I call the xoverlay function, I get a BAD WINDOW error and the application stops.
If I add the gtk_drawing_area into the GTK_FIXED after I call the xoverlay function, I get that the gtk drawin has no window or pixmap and it plays in its own window.

Here you have the code, I hope you can see what fails here:

container is a gtk_fixed added into the main window!




```
void iMovie::play(GtkWidget * container)
{

		 m_drawable = gtk_drawing_area_new();
		 gtk_widget_set_size_request (m_drawable, 600, 500);
		 gtk_fixed_put(GTK_FIXED(container),m_drawable,SHADOW_WIDTH,SHADOW_WIDTH+HEADER_HEIGHT);
		  		 
		 g_print("Start Playing (%s)...\n",g_file_get_uri ( m_gfile));

		 gst_init (NULL, NULL);

		 m_pipeline		 = gst_pipeline_new 	    	("gst-player");
		 m_bin 		 	 = gst_element_factory_make ("playbin", 	  "m_bin");
		 m_sink 		 = gst_element_factory_make ("xvimagesink",  "m_sink");
		 g_object_set ( G_OBJECT (m_bin), "video-sink", m_sink, NULL );
		 gst_bin_add  ( GST_BIN (m_pipeline), m_bin );


		 {
		 		 GstBus *bus;
		 		 bus = gst_pipeline_get_bus (GST_PIPELINE (m_pipeline));
		 		 gst_object_unref (bus);
		 }

		 
		 g_object_set (G_OBJECT (m_bin), "uri", g_file_get_uri( m_gfile), NULL );
		 g_object_set (G_OBJECT (m_sink), "force-aspect-ratio", TRUE, NULL  );
		 
    
    		 
 		if (GST_IS_X_OVERLAY (m_sink))
    		{
		 		 printf("Is Overlay (Win ID: %i)!!\n",GPOINTER_TO_INT(GDK_WINDOW_XWINDOW(m_drawable->window)));

		 		 gst_x_overlay_set_xwindow_id (GST_X_OVERLAY (m_sink), GPOINTER_TO_INT(GDK_WINDOW_XWINDOW(m_drawable->window)));
		 		 gst_x_overlay_handle_events  (GST_X_OVERLAY (m_sink), FALSE);
    		}
 
		 gst_element_set_state (m_pipeline, GST_STATE_PLAYING);
 		 
		 gtk_widget_show_all(container); 
```
}

---

