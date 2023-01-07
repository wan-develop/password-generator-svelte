<script>
	
	let passwordLength = 9;

	// Password Pattern Config
	let hasLowerCase = false;
	let hasUpperCase = false;
	let hasNumbers = true;
	let hasSymbols = false;
	
	//Password Chars
	let lowerCase = "abcdefghijklmnopqrstuvxwyz";
	let upperCase = lowerCase.toUpperCase()
	let numbers = "0123456789";
	let symbols = "!@#$%&*{}[]"
	
	let password = "G3n3r4T3"
	
	const generateNewPassword = () => {
		
		const passwordPattern = [
			( hasLowerCase ? lowerCase : ""),
			( hasUpperCase ? upperCase : ""),
			(hasNumbers ? numbers : ""),
			(hasSymbols ? symbols : "")
		]
		//Join All string into a single string
		let newPassword = passwordPattern.join("");
		
		//Gets numbers from Array of strings based on defined passwordLength
		let passwordArray = new Array(passwordLength).fill(0).map(char => 
				newPassword[ Math.round( Math.random() * newPassword.length) ]
		);
		password = passwordArray.join("");
		
	}
	
	$:{
		//Set min/max of passwordLength
		if( passwordLength >= 34 ) passwordLength = 50;
		else if( passwordLength <= 1) passwordLength = 1;
	}
	
</script>

<div class="App">
	<h1>Password Generator</h1>
	
    <!-- Password result here -->
    <h3>{password}</h3>
    
	
    <div id="password-length-field">
        <input id="length-input" type="number" bind:value={passwordLength}/>
        <span id="length-notification" >set password length</span>
    </div>
	<ul>
		<li>
			<label name="lower-case">
				<p>lower case</p>
				<input type="checkbox" bind:checked={hasLowerCase} for="lower-case"/>
			</label>
		</li>
		
		<li>
			<label name="upper-case">
				<p>upper case</p>
				<input type="checkbox" bind:checked={hasUpperCase} for="upper-case"/>
			</label>
		</li>
		<li>
			<label name="numbers-label">
				<p>numbers</p>
				<input type="checkbox" bind:checked={hasNumbers} for="numbers-label"/>
			</label>
			
		</li>
		
		<li>
			<label name="symbols-label">
				<p>simbols</p>
				<input type="checkbox" bind:checked={hasSymbols} for="symbols-label"/>
			</label>
			
		</li>
	
	</ul>
	
	
	
	<button on:click={generateNewPassword}>GENERATE</button>
	
    <a id="github-link" href="https://github.com/wan-develop" target="_blank" rel="noreferrer">
        <h3>My GitHub</h3>
    </a>


</div>

<style>
	
	.App {
		
		font-family: Consolas;
		
		display: flex;
		justify-content: center;
		align-items: center;
		flex-direction: column;
		background-image: linear-gradient(
			50deg,
			#111 300px,
			#111e,
			#111
		);
		color: white;
		
		width: 100vw;
		height: 100vh;

        margin: -8px;
		
		
		
	}

    /* NO-USER-SELECT */
    ul,button,h1 {
        user-select: none;
    }
	
	ul {
		display: flex;
		list-style: none;
	}

    #password-length-field {
        display: flex;
        justify-content: center;
    }

    input#length-input {
        text-align: center;
        width: 50px;
        padding: 5px 0;
        text-align: center;
    }

    input#length-input:hover + span#length-notification,
    input#length-input:focus + span#length-notification {
        opacity: 1 ;
    }

    #length-notification {
        position: absolute;
        background-color: #fff2;
        padding: 10px;
        border-radius: 10px;
        top: 10px;

        transition: opacity 400ms ease-in-out;

        opacity: 0;
        user-select: none;
        pointer-events: none;
    }

	label {
		display: flex;
		justify-content: center;
		align-items: center;
		min-width: 50px;
		max-height: 50px;
		margin: 5px;
		padding: 0px 20px;
		border: solid 1px white;
		border-radius: 1.5em;
	}
	
	label > p {
		display: inline; 
		color: white;
	}
	
	label > input[type="checkbox"] {
		display: none;
	}
	
	label:has(:checked) {
		background-color: #11ff11;
		color: white;
	}
	
	li {
		display: flex;
		align-items: center;
		width: 100px;
		}
	
	button {
		background-color: #222;
		color: white;
		border-radius: 2rem;
		min-width: 200px;
		min-height: 50px;
		
	}
	
	button:active {
		background-color: #11ff11;
	}

    button:hover,
    label:hover,
    label:hover > p {
        border-color: #11ff11;
        color: #11ff11;
    }

    #github-link {
        position: fixed;
        right: 10px;
        bottom: 10px;
    }

</style>
