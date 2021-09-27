#!/usr/bin/env python

import textwrap

from six.moves.BaseHTTPServer import BaseHTTPRequestHandler, HTTPServer


class HelloRequestHandler(BaseHTTPRequestHandler):

    def do_GET(self):
        if self.path != '/':
            self.send_error(404, "Object not found")
            return
        self.send_response(200)
        self.send_header('Content-type', 'text/html; charset=utf-8')
        self.end_headers()
        response_text = textwrap.dedent('''\
            &lt;html&gt;
            &lt;head&gt;
                &lt;title&gt;Hello World&lt;/title&gt;
            &lt;/head&gt;
            &lt;body&gt;
                &lt;h1&gt;Hello, World!&lt;/h1&gt;
                &lt;p&gt;... Here we are!&lt;/p&gt;
            &lt;/body&gt;
            &lt;/html&gt;
        ''')
        self.wfile.write(response_text.encode('utf-8'))


server_address = ('', 8000)
httpd = HTTPServer(server_address, HelloRequestHandler)
httpd.serve_forever()
