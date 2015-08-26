ORCA/MATRIX Demo Transport Library
==================================


<h1>
1. Introduction
</h1>
<p>Orca.js is a JavaScript API for supporting Real Time Communications (RTC) in web applications. Orca.js abstracts the implementation of RTC from the application allowing application code to be portable across different RTC providers. For more information go to:
</p>
<ul>
  <li><a href="http://www.orcajs.org">www.orcajs.org</a></li>
  <li><a href="https://github.com/orcajs/orca.js">github.com/orcajs/orca.js</a></li>
</ul>
<p>
Matrix is an open standard for decentralised communication, providing simple HTTP APIs and open source reference implementations for securely distributing and persisting JSON over an open federation of servers. For more information go to:
</p>
<ul>
<li><a href="http://matrix.org">matrix.org</a></li>
</ul>
<p>
   This project is an implementation of the Orca API for development, testing and experimentation purposes. This implementation of the API (sometimes called a "transport library") uses the Matrix system to exchange signalling between the endpoints though it is not compatible directly with the Matrix application RTC signalling. It is designed to support 2 party calls between endpoints. The implementation, as provided here, is not intended to be used in any kind of real applications. It does not provide good support for security or robustness features that would be required in real deployments. Both endpoints must run this transport library.
   </p>
<p>
 This demo application relies on:
</p>
<ul>
<li>
an available Matrix system. This version is hard-coded to use user ids in the "matrix.org" domain,
</li>
<li>
a transport library, which an implementation of the Orca API dedicated to the reflector protocol,
</li>
<li>
a simple example client application, which is a basic chat UI relying on the transport library.
</li>
</ul>
<p>
    This transport library is currently tested with the Chrome browser.
</p>
<p>
    This manual will give a description of the components and the way to get them configured and working in your environment.
</p>
<h1>
2. Quick start
</h1>
<p>
Download the repository in to a suitable directory on the host machine. Arrange, using any common web server, for the contents of the directory to be accessible on the web from a suitable URL.
</p>
<p>
You will need to create two user identities in the domain "matrix.org". This may be done at <A HREF="https://matrix.org/beta/#/register">https://matrix.org/beta/#/register</A>. Note the user IDs and the passwords for these two identities.
</p>
<p> 
Edit the file "demo1.htm" in a text editor. Change these values in the inputs as follows: 
</p>
<ul>
<li>"xxxx1" should be changed to the first user ID (without the matrix.org domain - so if your user id was "@matrixuser1:matrix.org" this field should read "matrixuser1").</li>
<li>"pppp1" should be changed to the password for the first user ID.</li>
<li>"xxxx2" should be changed to the second user ID (see notes above).
</ul>
<p> 
Edit the file "demo2.htm" in a text editor. Change these values in the inputs as follows: 
</p>
<ul>
<li>"xxxx2" should be changed to the second user ID (see notes above).</li>
<li>"pppp2" should be changed to the password for the second user ID.</li>
</ul>
<p>
Load the pages "demo1.htm" and "demo2.htm" in Chrome on different machines. Loading the page should automatically start a session with the Matrix server and this will be indicated in the status indication. Once both pages have loaded and the sessions have been established a call may be initiated from the "demo1" page to the "demo2" page by clicking the "connect" button. Accept the Chrome prompt to allow sharing of the microphone and camera. An alerting indication should start on the "demo2" page. The call may be accepted by clicking the "Accept Incoming Call" button.
</p>
<h1>3. Detailed Notes</h1>
<p>
This project has been constructed for demo purposes only and therefore has a number of limitations. Passwords are clearly visible to users with even moderate technical skills. Currently STUN and TURN are not used so both machines must normally be on the same LAN segment if media is to be exchanged. This implementation is limited to one call at a time and does not handle all error situations.
</p>
<p>
The signalling between the endpoints is not compatible with the Matrix application RTC signalling. To establish a call a new Matrix chat room is created and the second part is invited to join it. The library will automatically accept room invites from other Orca clients. Messages exchanged in this chat room consist of <A HREF="https://github.com/orcajs/reflector">Orca Reflector</A> messages packaged in to a Matrix message format.
</p>
<p>
For convenience this repository contains copies of the JQuery library and also the Matrix Web JS client. The latest version of the Matrix Web JS Client can be obtained from <A HREF="https://github.com/matrix-org/matrix-js-sdk">https://github.com/matrix-org/matrix-js-sdk</A></p> 
<h1>ORCA Open Source License Agreement:</h1>

Please review the Open Source License Agreement for ORCA: http://orcajs.org/license.html.
