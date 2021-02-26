# Fix-CORS start local project Asp.net Frameword mvc 5
Step 1: File Global.asax.cs add methor Application_BeginRequest()

	  protected void Application_BeginRequest()
		{
		    if (Request.HttpMethod == "OPTIONS")
		    {
			Response.StatusCode = (int)HttpStatusCode.OK;
			Response.End();
		    }
	  }

Step 2: add to file web.config

	<system.webServer>
		<httpProtocol>
			<customHeaders>
				<add name="Access-Control-Allow-Origin" value="http://localhost:3000" />
				<add name="Access-Control-Allow-Credentials" value="true" />
				<add name="Access-Control-Allow-Headers" value="Accept,Content-Type,CSRF-TOKEN,Refferer,User-Agent,X-CSRF-TOKEN" />
			</customHeaders>
		</httpProtocol>
		<modules runAllManagedModulesForAllRequests="true"></modules>
	</system.webServer>
  
  ## Note value "Access-Control-Allow-Headers" Optional follow request header client
