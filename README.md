allows-cross-domain-communication-from-the-browser
==================================================


Front End
---------
var formData = new FormData();
formData.append("name", "Groucho");
var xhr = new XMLHttpRequest();
//xhr = new XDomainRequest();// for IE
xhr.open("POST", "http://115.99.16.3/html/demo/data_json.php");
xhr.send(formData);
xhr.onload = function(){console.log(xhr.response)}

Back End
*****************************************************************************
Node.js
--------
 app.use(function (req, res, next) {

    /* Website you wish to allow to connect */
    res.setHeader('Access-Control-Allow-Origin', '*');

    /* Request methods you wish to allow */
    res.setHeader('Access-Control-Allow-Methods', 'GET, POST, OPTIONS, PUT, PATCH, DELETE');

    // Request headers you wish to allow
    res.setHeader('Access-Control-Allow-Headers', 'X-Requested-With,content-type');

    // Set to true if you need the website to include cookies in the requests sent
    // to the API (e.g. in case you use sessions)
    res.setHeader('Access-Control-Allow-Credentials', true);

    // Pass to next layer of middleware
    next();
});



PHP
--------------------------------------
<?php
//header('Access-Control-Allow-Origin: http://sagarpanda.com');
header('Access-Control-Allow-Origin: *');
//header('Access-Control-Allow-Methods: GET, POST, PUT');
//header('Access-Control-Allow-Credentials: true');
//header('Access-Control-Allow-Headers: Origin, X-Requested-With, Content-Type, Accept');//to work in sencha touch ajax call
echo '{"name":"'.$_POST[name].'","status":true}';
?>

.net backend
------------
<httpProtocol>
  <customHeaders>
    <add name="Access-Control-Allow-Origin" value="*" />
    <add name="Access-Control-Allow-Headers" value="Origin, X-Requested-With, Content-Type, Accept" />
  </customHeaders>
</httpProtocol>


ref:-
http://www.html5rocks.com/en/tutorials/cors/
https://developer.mozilla.org/es/docs/XMLHttpRequest/Usar_XMLHttpRequest
