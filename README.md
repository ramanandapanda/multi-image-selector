## multi-image-selector
multi-image-selector android for react-native

# 1.npm Install (required)
	npm i react-native-multi-image-selector --save 
# Android:
## 2. Automatic Installation
	react-native link 
## 2.Manual installation
 
	//  edit: android/settings.gradle
	include ':react-native-multi-image-selector'
	project(':react-native-multi-image-selector').projectDir = new File(settingsDir, '../node_modules/react-native-multi-image-selector/android')

---
	//  edit : android/app/build.gradle
	...
	
	dependencies {
	    ...
	    compile project(':react-native-multi-image-selector')
	}
---
	//  edit : android/app/src/main/java/com/<...>/MainApplication.java
	...
	
	import me.nereo.multi_image_selector.MultiImagePackage; // <-- add this import
	
	public class MainApplication extends Application implements ReactApplication {
	    @Override
	    protected List<ReactPackage> getPackages() {
	        return Arrays.<ReactPackage>asList(
	            new MainReactPackage(),
	            new MultiImagePackage()// <-- add this line 添加这行
	        );
	    }
	...
	}	
## Usage:
![loading](Example/camera.gif) ![loading](Example/multiple.gif) 
<table>
	<tr>
		<th>Props</th>
		<th>Default</th>
		<th>type</th>
		<th>Descriptio</th>
	</tr>
	<tr>
		<td>showCamera</td>
		<td>true</td>
		<td>bool</td>	
		<td> show camera?</td>	
	</<tr> 
	<tr>
		<td>maxNum</td>
		<td>5</td>
		<td>number</td>	
		<td> max select image number</td>	
	</<tr> 
	<tr>
		<td>multiple</td>
		<td>true</td>
		<td>bool</td>	
		<td> Whether open multi-select</td>	
	</<tr>
	<tr>
		<td>cropping</td>
		<td>false</td>
		<td>bool</td>	
		<td> Whether crop</td>	
	</<tr> 
	<tr>
		<td>width</td>
		<td>100</td>
		<td>number</td>	
		<td> crop result width</td>	
	</<tr> 
	<tr>
		<td>height</td>
		<td>100</td>
		<td>number</td>	
		<td> crop result width</td>	
	</<tr> 
</table>

`
	export default class MyProject extends Component {
	    constructor() {
	        super();
	        this.state = {
	            imageArray: []
	        }
	    }
	
	    render() {
	        return (
	            <TouchableNativeFeedback style={styles.container}
	                 onPress={()=> {
	                     MultiImage.pickImage({
	                         showCamera:true,
	                         maxNum: 5,
	                         multiple:true
	                     }).then((imageArray)=> {
	                         this.setState({imageArray})
	                     }).catch(e=> {
	                    });
	             }}>
	                <View style={styles.container}>
	                    <TouchableNativeFeedback style={{margin: 5}} onPress={()=> {
	                        this.setState({imageArray: []})
	                    }}><Text>Clear</Text></TouchableNativeFeedback>
	                    <ScrollView style={{flex: 1}}>
	                        {this.state.imageArray.map(data=> {
	                            return (<Image source={{uri: data}} style={{width: 200, height: 200}}/>)
	                        })}
	                    </ScrollView>
	                </View>
	            </TouchableNativeFeedback>
	        );
	    }
	}

`
